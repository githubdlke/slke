---
title: Cancelar un flujo de trabajo
intro: 'Puedes cancelar una ejecución de flujo de trabajo que esté en curso. Cuando cancelas una ejecución de flujo de trabajo, {% data variables.product.prodname_dotcom %} cancela todsos los jobs y pasos que son parte de ésta.'
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
ms.openlocfilehash: f8bf0d06f5e0e37cb120b22a3bd6da39b51b78a9
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '145091854'
---
{% data reusables.actions.enterprise-beta %} {% data reusables.actions.enterprise-github-hosted-runners %}

{% data reusables.repositories.permissions-statement-write %}

## Cancelar una ejecución de flujo de trabajo

{% data reusables.repositories.navigate-to-repo %} {% data reusables.repositories.actions-tab %} {% data reusables.repositories.navigate-to-workflow %}
1. Desde la lista de ejecuciones de flujo de trabajo, haga clic en el nombre de la ejecución de `queued` o `in progress` que quiera cancelar.
![Nombre de la ejecución de flujo de trabajo](/assets/images/help/repository/in-progress-run.png)
1. En la esquina superior derecha del flujo de trabajo, haga clic en **Cancelar flujo de trabajo**.
![Botón Cancelar conjunto de comprobaciones](/assets/images/help/repository/cancel-check-suite-updated.png)

## Pasos que toma {% data variables.product.prodname_dotcom %} para cancelar una ejecución de flujo de trabajo

Cuando cancelas una ejecución de flujo de trabajo, tal vez estés ejecutando otro software que utiliza recursos que se relacionan con ésta. Para ayudarte a liberar los recursos relacionados con dicha ejecución de flujo de trabajo, podría ser útil entender los pasos que realiza {% data variables.product.prodname_dotcom %} para cancelar una ejecución de flujo de trabajo.

1. Para cancelar una ejecución de flujo de trabajo, el servidor vuelve a evaluar las condiciones `if` para todos los trabajos que se ejecutan actualmente. Si la condición se evalúa como `true`, el trabajo no se cancelará. Por ejemplo, la condición `if: always()` se evaluaría como true y el trabajo continúa en ejecución. Cuando no hay condición, es equivalente a una condición `if: success()`, que solo se ejecuta si el paso anterior ha finalizado correctamente.
2. Para los jobs que necesitan cancelarse, el servidor envía un mensaje de cancelación a todas las máquinas ejecutoras con jobs que necesitan cancelarse.
3. Para los trabajos que siguen en ejecución, el servidor vuelve a evaluar las condiciones `if` para los pasos sin finalizar. Si la condición se evalúa como `true`, el paso continúa ejecutándose.
4. Para los pasos que se deben cancelar, la máquina del ejecutor envía `SIGINT/Ctrl-C` al proceso de entrada del paso (`node` para la acción javascript, `docker` para la acción contenedora y `bash/cmd/pwd` cuando se usa `run` en un paso). Si el proceso no sale en 7500 ms, el ejecutor enviará `SIGTERM/Ctrl-Break` al proceso y, después, esperará 2500 ms hasta que el proceso salga. Si el proceso aún está ejecutándose, el ejecutor finalizará abruptamente el árbol de proceso.
5. Después de los 5 minutos del periodo de expiración de plazo de cancelación, el servidor forzará la terminación de todos los jobs y pasos que no hayan finalizado la ejecución o que hayan fallado en completar el proceso de cancelación.

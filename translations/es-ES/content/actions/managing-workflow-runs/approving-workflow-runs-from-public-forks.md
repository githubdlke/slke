---
title: Aprobar ejecuciones de flujo de trabajo desde bifurcaciones públicas
intro: 'Cuando un contribuyente externo emite una solicitud de cambios a un repositorio público, podría ser que un mantenedor con acceso de escritura tenga que aprobar cualquier ejecución de flujo de trabajo.'
versions:
  fpt: '*'
  ghec: '*'
shortTitle: Approve public fork runs
ms.openlocfilehash: b995362f67d97a3e2ee6d1029cbe24227867f58a
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '145091824'
---
## Acerca de las ejecuciones de flujo de trabajo de las bifurcaciones públicas

{% data reusables.actions.workflow-run-approve-public-fork %}

Puede configurar los requisitos de aprobación de flujo de trabajo para un [repositorio](/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#configuring-required-approval-for-workflows-from-public-forks), una [organización](/organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#configuring-required-approval-for-workflows-from-public-forks) o una [empresa](/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise#enforcing-a-policy-for-fork-pull-requests-in-your-enterprise).

Las ejecuciones de flujos de trabajo que hayan estado esperando una aprobación por más de 30 días se borrarán automáticamente.

## Aprobar las ejecuciones de flujo de trabajo en una solicitud de cambios de una bifurcación pública

Los mantenedores con acceso de escritura en un repositorio pueden utilizar el siguiente procedimiento para revisar y ejecutar flujos de trabajo en las solicitudes de extracción de los contribuyentes que requieran aprobación.

{% data reusables.repositories.sidebar-pr %} {% data reusables.repositories.choose-pr-review %} {% data reusables.repositories.changed-files %}
1. Inspecciona los cambios propuestos en la solicitud de cambios y asegúrate de que estés de acuerdo para ejecutar tus flujos de trabajo en la rama de la solicitud de cambios. Debe estar especialmente alerta de los cambios propuestos en el directorio `.github/workflows/` que afecten a los archivos de flujo de trabajo.
1. Si está familiarizado con la ejecución de flujos de trabajo en la rama de solicitud de incorporación de cambios, vuelva a la pestaña {% octicon "comment-discussion" aria-label="The discussion icon" %} **Conversación** y, en "Flujos de trabajo en espera de aprobación", haga clic en **Aprobar y ejecutar**.

   ![Aprueba y ejecuta flujos de trabajo](/assets/images/help/pull_requests/actions-approve-and-run-workflows-from-fork.png)

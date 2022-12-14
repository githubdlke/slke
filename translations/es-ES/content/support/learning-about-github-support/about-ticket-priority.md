---
title: Acerca de la prioridad de los tickets
intro: Puedes comunicar la severidad de tu problema y la forma en la que está afectándote a ti y a tu equipo si configuras la prioridad de tu ticket de soporte.
shortTitle: Ticket priority
versions:
  ghec: '*'
  ghes: '*'
  ghae: '*'
topics:
  - Support
ms.openlocfilehash: bce2a30ad25b93274e982991f81be5b1b796c685
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '145140098'
---
Cuando contactas al {% data variables.contact.enterprise_support %}, puedes elegir una de {% ifversion ghes or ghae %}cuatro{% else %}tres{% endif %} prioridades para el ticket: {% ifversion ghes or ghae %}{% data variables.product.support_ticket_priority_urgent %},{% endif %} {% data variables.product.support_ticket_priority_high %}, {% data variables.product.support_ticket_priority_normal %} o {% data variables.product.support_ticket_priority_low %}.

{% ifversion ghes or ghae %}

{% data reusables.support.github-can-modify-ticket-priority %}

{% ifversion ghes %}

## Prioridad de los tickets para {% data variables.product.prodname_ghe_server %}

{% data reusables.support.ghes-priorities %}

## Prioridad de los tickets para la {% data variables.product.prodname_advanced_security %}

| Prioridad | Descripción |
| :---: | --- |
| {% data variables.product.support_ticket_priority_high %} | {% data variables.product.prodname_advanced_security %} no funciona o se detiene o se ve gravemente afectado de tal manera que el usuario final no puede seguir utilizando el software razonablemente y no hay solución disponible para solucionar el problema. |
| {% data variables.product.support_ticket_priority_normal %} | {% data variables.product.prodname_advanced_security %} está funcionando de forma inconsistente, lo que provoca un deterioro de la productividad y el uso del usuario final. |
| {% data variables.product.support_ticket_priority_low %} | {% data variables.product.prodname_advanced_security %} funciona consistentemente, pero el usuario final solicita cambios menores en el software, tales como actualizaciones de documentación, defectos cosméticos o mejoras.|

{% elsif ghae %} {% data reusables.support.ghae-priorities %} {% endif %}

{% elsif ghec %}

<!-- /github/working-with-github-support/github-enterprise-cloud-support.md -->

{% data reusables.support.zendesk-old-tickets %}

Puedes enviar preguntas prioritarias si has comprado {% data variables.product.prodname_ghe_cloud %} o si eres miembro, colaborador externo o gerente de facturación de una organización {% data variables.product.prodname_dotcom %} actualmente suscrita en {% data variables.product.prodname_ghe_cloud %}.

Preguntas que califican para recibir respuestas prioritarias:
- Incluyen preguntas relacionadas con tu imposibilidad para acceder o usar la funcionalidad de control de la versión principal de {% data variables.product.prodname_dotcom %}
- Incluyen situaciones relacionadas con la seguridad de tu cuenta
- No incluyen servicios y funciones periféricos, como preguntas acerca de Gists, {% data variables.product.prodname_pages %} o notificaciones de correo electrónico
- Incluyen preguntas acerca de organizaciones que actualmente usan {% data variables.product.prodname_ghe_cloud %}

Para calificar para una respuesta prioritaria, debes hacer lo siguiente:
- Enviar la pregunta a [{% data variables.contact.enterprise_support %}](https://support.github.com/contact?tags=docs-generic) desde una dirección de correo electrónico verificada asociada a una organización que actualmente use {% data variables.product.prodname_ghe_cloud %}
- Enviar un ticket de asistencia nuevo para cada situación prioritaria particular
- Enviar tu pregunta de lunes a viernes en tu zona horaria local
- Comprender que la respuesta a una pregunta prioritaria será recibida por correo electrónico
- Colaborar con {% data variables.contact.github_support %} y proporcionar toda la información que solicite {% data variables.contact.github_support %}

{% note %}

**Nota:** Las preguntas no recibirán respuestas prioritarias si se envían durante un festivo local en su jurisdicción.

{% endnote %}

El tiempo de respuesta objetivo de ocho horas:
- Comienza cuando {% data variables.contact.github_support %} recibe tu pregunta que califica
- No comienza hasta que hayas proporcionada la suficiente información para responder la pregunta, a menos que específicamente indiques que no cuentas con la información suficiente
- No aplica durante los fines de semana de tu zona horaria local o durante los feriados locales de tu jurisdicción

{% note %}

**Nota:** {% data variables.contact.github_support %}no garantiza una resolución para la pregunta prioritaria. {% data variables.contact.github_support %} puede escalar problemas al estado de pregunta prioritaria o bajarlos en función de nuestra evaluación razonable de la información que nos proporcionas.

{% endnote %}

{% endif %}

## Información adicional

- "[Creación de una incidencia de soporte técnico](/support/contacting-github-support/creating-a-support-ticket)"

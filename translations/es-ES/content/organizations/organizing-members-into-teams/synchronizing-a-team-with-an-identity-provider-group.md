---
title: Sincronizar un equipo con un grupo de proveedor de identidad
intro: 'Puedes sincronizar un equipo de {% data variables.product.product_name %} con un grupo de proveedor de identidad (IdP) compatible para agregar y eliminar miembros del grupo automáticamente.'
redirect_from:
  - /github/setting-up-and-managing-organizations-and-teams/synchronizing-a-team-with-an-identity-provider-group
permissions: 'Organization owners and team maintainers can synchronize a {% data variables.product.prodname_dotcom %} team with an IdP group.'
versions:
  ghae: '*'
  ghec: '*'
  feature: scim-for-ghes
topics:
  - Organizations
  - Teams
shortTitle: Synchronize with an IdP
ms.openlocfilehash: c4ea8dc13eee674b962108ba52c71e67e8462b87
ms.sourcegitcommit: f638d569cd4f0dd6d0fb967818267992c0499110
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2022
ms.locfileid: '148106985'
---
{% data reusables.enterprise-accounts.emu-scim-note %}

## Acerca de la sincronización de equipo

{% data reusables.identity-and-permissions.about-team-sync %}

{% ifversion ghec %}Puedes conectar hasta cinco grupos de IdP a un equipo de {% data variables.product.product_name %}.{% elsif ghae %}Puedes conectar a un equipo de {% data variables.product.product_name %} a un grupo de IdP. Todos los usuarios en el grupo se agregan automáticamente al equipo y también a la organización padre como miembros. Cuando desconectas a un grupo de un equipo, los usuarios que se convirtieron en miembros de la organización a través de una membrecía de equipo se eliminan de dicha organización.{% endif %} Puedes asignar un grupo de IdP a varios equipos de {% data variables.product.product_name %}.

{% ifversion ghec %}La sincronización de equipos no es compatible con grupos de IdP con más de 5000 miembros.{% endif %}

Una vez que un equipo de {% data variables.product.prodname_dotcom %} se conecta a un grupo de IdP, tu administrador de IdP debe hacer cambios en la membrecía del equipo a través del proveedor de identidad. No puedes administrar las membrecías de equipo en {% data variables.product.product_name %}{% ifversion ghec %} ni utilizando la API{% endif %}.

{% ifversion ghec %}{% data reusables.enterprise-accounts.team-sync-override %}{% endif %}

{% ifversion ghec %} Todos los cambios de membrecía que se hagan a través de tu IdP aparecerán en la bitácora de auditoría en {% data variables.product.product_name %} como cambios realizados por el bot de sicnronización de equipos. Tu IdP enviará datos de la membrecía de equipo a {% data variables.product.prodname_dotcom %} una vez cada hora.
Conectar un equipo a un grupo IdP puede eliminar a algunos miembros del equipo. Para obtener más información, consulta "[Requisitos para los miembros de los equipos sincronizados](#requirements-for-members-of-synchronized-teams)".
{% endif %}

{% ifversion ghae %} Cuando cambia la membrecía de grupo en tu IdP, este envía una solicitud de SCIM con los cambios a {% data variables.product.product_name %} de acuerdo con la programación que determinó tu IdP. Cualquier solicitud que cambie la membrecía de organización o equipo de {% data variables.product.prodname_dotcom %} se registrará en la bitácora de auditoría como cambios que realizó la cuenta que se utilizó para configurar el aprovisionamiento de usuarios. Para obtener más información sobre esta cuenta, consulta "[Configuración del aprovisionamiento de usuarios para la empresa](/admin/authentication/configuring-user-provisioning-for-your-enterprise)". Para obtener más información sobre las programaciones de solicitudes SCIM, consulta "[Comprobación del estado del aprovisionamiento de usuarios](https://docs.microsoft.com/en-us/azure/active-directory/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user)" en Microsoft Docs. {% endif %}

Los equipos padre no pueden sincronizarse con los grupos de IdP. Si el equipo que quieres conectar a un grupo de IdP es un equipo padre, te recomendamos crear un equipo nuevo o eliminar las relaciones anidadas que hacen de tu equipo un equipo padre. Para obtener más información, consulta "[Acerca de los equipos](/articles/about-teams#nested-teams)", "[Creación de un equipo](/organizations/organizing-members-into-teams/creating-a-team)" y "[Traslado de un equipo en la jerarquía de la organización](/articles/moving-a-team-in-your-organizations-hierarchy)".

Para administrar el acceso de un repositorio para cualquier equipo de {% data variables.product.prodname_dotcom %}, incluyendo los equipos conectados a un grupo de IdP debes hacer cambios con {% data variables.product.product_name %}. Para obtener más información, consulta "[Acerca de los equipos](/articles/about-teams)" y "[Administración del acceso de equipo a un repositorio de la organización](/articles/managing-team-access-to-an-organization-repository)". 

{% ifversion ghec %}También puedes administrar la sincronización de equipos con la API. Para obtener más información, consulta "[Sincronización de equipos](/rest/reference/teams#team-sync)".{% endif %}

{% ifversion ghec %}
## Requisitos para los miembros de los equipos sincronizados

Después de conectar un equipo a un grupo IdP, la sincronización de equipos agregará a cada miembro del grupo de IdP al equipo correspondiente en {% data variables.product.product_name %} solo si:
- La persona es miembro de la organización en {% data variables.product.product_name %}.
- La persona ya ha iniciado sesión con su cuenta personal en {% data variables.product.product_name %} y se ha autenticado por lo menos una vez en la cuenta de la organización o la empresa mediante el inicio de sesión único SAML.
- La identidad de SSO de la persona es miembro del grupo de IdP.  

Los equipos o miembros del grupo existentes que no cumplan con estos criterios se eliminarán automáticamente del equipo en {% data variables.product.product_name %} y perderán acceso a los repositorios. El revocar la identidad ligada a un usuario también eliminará a dicho usuario de cualquier equipo que se encuentre mapeado en los grupos de IdP. Para obtener más información, consulta "[Visualización y administración del acceso SAML de un miembro a la organización](/organizations/granting-access-to-your-organization-with-saml-single-sign-on/viewing-and-managing-a-members-saml-access-to-your-organization#viewing-and-revoking-a-linked-identity)" y "[Visualización y administración del acceso SAML de un usuario a la empresa](/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/viewing-and-managing-a-users-saml-access-to-your-enterprise#viewing-and-revoking-a-linked-identity)".

Puedes volver a agregar automáticamente a aquellos miembros del equipo que hayas eliminado una vez que se autentiquen en la cuenta empresarial u organizacional utilizando el SSO y así se migren al grupo de IdP conectado.

Para evitar eliminar miembros del equipo accidentalmente, te recomendamos requerir el SSO de SAML en tu cuenta organizacional o empresarial mediante la creación de nuevos equipos para sincronizar datos de membrecías y revisar la membrecía del grupo de IdP antes de que sincronices a los equipos existentes. Para obtener más información, consulta "[Aplicación del inicio de sesión único de SAML para la organización](/articles/enforcing-saml-single-sign-on-for-your-organization)" y "[Configuración del inicio de sesión único de SAML para la empresa](/enterprise-cloud@latest/admin/authentication/managing-identity-and-access-for-your-enterprise/configuring-saml-single-sign-on-for-your-enterprise)".

{% endif %}

## Prerrequisitos

{% ifversion ghec %} Antes de poder conectar a un equipo de {% data variables.product.product_name %} con un grupo de proveedores de identidades, un propietario de empresa u organización debe habilitar la sincronización de equipos para tu cuenta empresarial o de la organización. Para obtener más información, consulta "[Administración de la sincronización de equipos para la organización](/organizations/managing-saml-single-sign-on-for-your-organization/managing-team-synchronization-for-your-organization)" y "[Administración de la sincronización de equipos para las organizaciones de la cuenta empresarial](/enterprise-cloud@latest/admin/authentication/managing-identity-and-access-for-your-enterprise/managing-team-synchronization-for-organizations-in-your-enterprise)".

Para evitar el eliminar miembros del equipo accidentalmente, visita el protal administrativo para tu IdP y confirma que cada miembro actual del equipo también se encuentre en los grupos de IdP que quieras conectar a este equipo. Si no tienes este acceso a tu proveedor de identidad, puedes comunicarte con tu administrador de IdP.

Debes autenticarte utilizando el SSO de SAML. Para obtener más información, consulta "[Autenticación con el inicio de sesión único de SAML](/articles/authenticating-with-saml-single-sign-on)".

{% elsif ghae %} Para poder conectar a un equipo de {% data variables.product.product_name %} con un grupo de IdP, primero debes configurar el aprovisionamiento de usuarios de {% data variables.location.product_location %} usando un sistema compatible con System for Cross-domain Identity Management (SCIM). Para obtener más información, consulta "[Configuración del aprovisionamiento de usuarios para la empresa](/admin/authentication/configuring-user-provisioning-for-your-enterprise)".

Una vez que se configure el aprovisionamiento de usuarios para {% data variables.product.product_name %} utilizando SCIM, puedes asignar la aplicación de {% data variables.product.product_name %} a cada grupo de IdP que quieras utilizar en {% data variables.product.product_name %}. Para obtener más información, consulta [Configuración del aprovisionamiento automático de usuarios para GitHub AE](https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/github-ae-provisioning-tutorial#step-5-configure-automatic-user-provisioning-to-github-ae) en Microsoft Docs.

{% elsif scim-for-ghes %} Debes configurar el aprovisionamiento de usuarios con SCIM de {% data variables.location.product_location %}. Para obtener más información, consulta "[Configuración del aprovisionamiento de usuarios con SCIM para la empresa](/admin/identity-and-access-management/using-saml-for-enterprise-iam/configuring-user-provisioning-with-scim-for-your-enterprise)".

{% data reusables.scim.ghes-beta-note %} {% endif %}

## Conectar un grupo de IdP a tu equipo

Cuando conectas un grupo de IdP a un equipo de {% data variables.product.product_name %}, todos los usuarios en el grupo se agregan automáticamente al equipo. {% ifversion ghae %}Cualquier usuario que no fuera un miembro de aquellos de la organización desde antes también se agregará a esta.{% endif %}

{% data reusables.profile.access_org %} {% data reusables.user-settings.access_org %} {% data reusables.organizations.specific_team %} {% data reusables.organizations.team_settings %} {% ifversion ghec %}
6. Debajo de "Grupos del Proveedor de Identidad", utiliza el menú desplegable y selecciona hasta 5 grupos del proveedor de identidad.
    ![Menú desplegable para elegir grupos de proveedores de identidades](/assets/images/help/teams/choose-an-idp-group.png){% elsif ghae %}
6. Debajo de "Grupo del Proveedor de Identidad", utiliza el menú desplegable y selecciona un grupo de proveedor de identidad de la lista.
    ![Menú desplegable para elegir un grupo de proveedor de identidades](/assets/images/enterprise/github-ae/teams/choose-an-idp-group.png){% endif %}
7. Haga clic en **Guardar cambios**.

## Desconectar un grupo de IdP de un equipo

Si desconectas un grupo de IdP de un equipo de {% data variables.product.prodname_dotcom %}, los miembros de este equipo que fueran asignados al equipo {% data variables.product.prodname_dotcom %} a través del grupo de IdP se eliminarán de dicho equipo. {% ifversion ghae %} Cualquier usuario que fuera miembro de la organización padre únicamente debido a esa conexión de equipo también se eliminará de la organización.{% endif %}

{% data reusables.profile.access_org %} {% data reusables.user-settings.access_org %} {% data reusables.organizations.specific_team %} {% data reusables.organizations.team_settings %} {% ifversion ghec %}
6. Debajo de "Grupos del Proveedor de Identidad", a la derecha del grupo de IdP que quieras desconectar, da clic en {% octicon "x" aria-label="X symbol" %}. 
    ![Anulación de la selección de un grupo de IdP conectado desde el equipo de GitHub](/assets/images/help/teams/unselect-idp-group.png){% elsif ghae %}
6. Debajo de "Grupo del Proveedor de Identidad", a la derecha del grupo de IdP que quieras desconectar, da clic en {% octicon "x" aria-label="X symbol" %}. 
    ![Anulación de la selección de un grupo de IdP conectado desde el equipo de GitHub](/assets/images/enterprise/github-ae/teams/unselect-idp-group.png){% endif %}
7. Haga clic en **Guardar cambios**.

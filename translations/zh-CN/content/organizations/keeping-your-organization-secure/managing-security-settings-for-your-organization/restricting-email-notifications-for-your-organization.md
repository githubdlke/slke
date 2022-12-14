---
title: 限制组织的电子邮件通知
intro: 为防止组织信息泄露到个人电子邮件帐户，您可以限制成员可以接收有关组织活动的电子邮件通知的域。
permissions: Organization owners can restrict email notifications for an organization.
redirect_from:
  - /articles/restricting-email-notifications-about-organization-activity-to-an-approved-email-domain
  - /articles/restricting-email-notifications-to-an-approved-domain
  - /github/setting-up-and-managing-organizations-and-teams/restricting-email-notifications-to-an-approved-domain
  - /organizations/keeping-your-organization-secure/restricting-email-notifications-to-an-approved-domain
  - /organizations/keeping-your-organization-secure/restricting-email-notifications-for-your-organization
versions:
  ghes: '*'
  ghec: '*'
type: how_to
topics:
  - Enterprise
  - Notifications
  - Organizations
  - Policy
shortTitle: Restrict email notifications
ms.openlocfilehash: 480f587862e0618c0624eec581520343c54afa35
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2022
ms.locfileid: '147060096'
---
## 关于电子邮件限制

当在组织中启用受限制的电子邮件通知时，成员只能使用与已验证或批准的域关联的电子邮件地址接收有关组织活动的电子邮件通知。 有关详细信息，请参阅“[验证或批准组织的域](/organizations/managing-organization-settings/verifying-or-approving-a-domain-for-your-organization)”。

{% ifversion ghec %} {% note %}

注意：要限制电子邮件通知，组织必须使用 {% data variables.product.prodname_ghe_cloud %}。 {% data reusables.enterprise.link-to-ghec-trial %}

{% endnote %} {% endif %}

{% data reusables.notifications.email-restrictions-verification %}

外部协作者不受限于已验证或批准域的电子邮件通知。 有关外部协作者的详细信息，请参阅“[组织中的角色](/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization#outside-collaborators)”。

如果您的组织由企业帐户拥有，则组织成员除了能够接收来自组织的任何已验证或批准域的通知之外，还能够接收来自企业帐户的任何已验证或批准域的通知。 有关详细信息，请参阅“[验证或批准企业的域](/admin/configuration/configuring-your-enterprise/verifying-or-approving-a-domain-for-your-enterprise)”。

## 限制电子邮件通知

在限制组织的电子邮件通知之前，您必须至少验证或批准组织的一个域名，或者企业所有者必须已验证或批准至少一个企业帐户域。

有关验证和批准组织域的详细信息，请参阅“[验证或批准组织的域](/organizations/managing-organization-settings/verifying-or-approving-a-domain-for-your-organization)”。

{% data reusables.profile.access_org %} {% data reusables.profile.org_settings %} {% data reusables.organizations.verified-domains %} {% data reusables.organizations.restrict-email-notifications %}
6. 单击“保存” 。

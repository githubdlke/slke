---
title: Acerca de las agrupaciones
intro: 'La agrupación {% data variables.product.prodname_ghe_server %} permite que los servicios que la componen {% data variables.product.prodname_ghe_server %} sean escalados a múltiples nodos.'
redirect_from:
  - /enterprise/admin/clustering/overview
  - /enterprise/admin/clustering/about-clustering
  - /enterprise/admin/clustering/clustering-overview
  - /enterprise/admin/enterprise-management/about-clustering
  - /admin/enterprise-management/about-clustering
versions:
  ghes: '*'
type: overview
topics:
  - Clustering
  - Enterprise
ms.openlocfilehash: 5da017898f1f0e205685dcf1fc29b5088030421a
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '146332484'
---
## Arquitectura de agrupación

{% data variables.product.prodname_ghe_server %} está compuesto por un conjunto de servicios. En una agrupación, estos servicios se ejecutan en múltiples nodos y las solicitudes son un balanceador de carga entre ellos. Los cambios se almacenan automáticamente con copias redundantes en nodos separados. La mayoría de los servicios son pares iguales con otras instancias del mismo servicio. Las excepciones a esto son los servicios `mysql-server` y `redis-server`. Funcionan con un único nodo _primario_ con uno o varios nodos de _réplica_.

Obtenga más información sobre [los servicios necesarios para la agrupación en clústeres](/enterprise/admin/enterprise-management/about-cluster-nodes#services-required-for-clustering).

## ¿Es adecuada la agrupación para mi organización?

{% data reusables.enterprise_clustering.clustering-scalability %} Sin embargo, la configuración de un agrupación redundante y escalable puede ser compleja y requiere de una planificación cuidadosa. Se deberá planificar esta complejidad adicional para situaciones durante la instalación, situaciones de recuperación ante desastre y actualizaciones.

{% data variables.product.prodname_ghe_server %} requiere una baja latencia entre los nodos y no está hecho para redundancia en todas las ubicaciones geográficas.

La agrupación brinda redundancia, pero no pretende reemplazar una configuración de Alta disponibilidad. Para obtener más información, consulte "[Configuración de alta disponibilidad](/enterprise/admin/guides/installation/configuring-github-enterprise-server-for-high-availability)". Una configuración de conmutación primaria/secundaria es mucho más simple que la agrupación y permitirá satisfacer las necesidades de muchas organizaciones. Para obtener más información, consulte [Diferencias entre la agrupación en clústeres y la alta disponibilidad](/enterprise/admin/guides/clustering/differences-between-clustering-and-high-availability-ha/).

{% data reusables.package_registry.packages-cluster-support %}

## ¿Cómo obtengo acceso a la agrupación?

La agrupación está diseñada para situaciones de escalada específica y no pretende ser usada para cada organización. Si te gustaría considerar la agrupación, por favor contacta a tu representante dedicado o a {% data variables.contact.contact_enterprise_sales %}.

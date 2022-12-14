---
title: Solucionar problemas de dominios personalizados y Páginas de GitHub
intro: 'Puedes buscar errores comunes para resolver los problemas que existan con los dominios personalizados o HTTPS para tu sitio de {% data variables.product.prodname_pages %}.'
redirect_from:
  - /articles/my-custom-domain-isn-t-working
  - /articles/custom-domain-isn-t-working
  - /articles/troubleshooting-custom-domains
  - /articles/troubleshooting-custom-domains-and-github-pages
  - /github/working-with-github-pages/troubleshooting-custom-domains-and-github-pages
product: '{% data reusables.gated-features.pages %}'
versions:
  fpt: '*'
  ghec: '*'
topics:
  - Pages
shortTitle: Troubleshoot a custom domain
ms.openlocfilehash: ce6251dbe96d531462c5c664dc9000f138059889
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '147428392'
---
## Errores de _CNAME_

{% ifversion pages-custom-workflow %}Si publicas desde un flujo de trabajo de {% data variables.product.prodname_actions %} personalizado, se omite cualquier archivo _CNAME_ y no es necesario.{% endif %}

Si publicas desde una rama, los dominios personalizados se almacenan en un archivo _CNAME_ en la raíz de la fuente de publicación. Puedes agregar o actualizar este archivo a través de la configuración del repositorio o manualmente. Para obtener más información, consulte "[Administración de un dominio personalizado para el sitio de {% data variables.product.prodname_pages %}](/articles/managing-a-custom-domain-for-your-github-pages-site)".

Para que su sitio se represente en el dominio correcto, es importante asegurarse de que el archivo _CNAME_ aún exista en el repositorio. Por ejemplo, muchos generadores de sitios estáticos realizan envíos de cambios forzosos al repositorio que pueden sobrescribir el archivo _CNAME_ que se agregó al repositorio cuando configuró su dominio personalizado. Si compila el sitio de manera local y envía los archivos generados a {% data variables.product.product_name %}, asegúrate de incorporar primero la confirmación que agregó el archivo _CNAME_ al repositorio local. De este modo, el archivo se incluirá en la compilación.

A continuación, asegúrese de que el archivo _CNAME_ tenga el formato correcto.

- El nombre de archivo _CNAME_ debe estar en mayúsculas.
- El archivo _CNAME_ solo puede contener un dominio. Para apuntar múltiples dominios a tu sitio, debes configurar un redireccionamiento a través de tu proveedor DNS.
- El archivo _CNAME_ solo debe contener el nombre de dominio. Por ejemplo, `www.example.com`, `blog.example.com` o `example.com`.
- El nombre de dominio debe ser único a lo largo de todos los sitios de {% data variables.product.prodname_pages %}. Por ejemplo, si el archivo _CNAME_ de otro repositorio contiene `example.com`, no puede usar `example.com` en el archivo _CNAME_ de su repositorio.

## Error de configuración DNS

Si tienes problemas para apuntar el dominio predeterminado para tu sitio a tu dominio personalizado, contáctate con tu proveedor DNS.

También puedes utilizar uno de los siguientes métodos para probar si los registros de DNS de tus dominios personalizados están configurados correctamente:

- Una herramienta de la CLI, como `dig`. Para obtener más información, consulte "[Administración de un dominio personalizado para el sitio de {% data variables.product.prodname_pages %}](/articles/managing-a-custom-domain-for-your-github-pages-site)".
- Una herramienta de búsqueda de DNS en línea.

## Nombres de dominios personalizados que no son compatibles

Si tu dominio personalizado no es compatible, puede que debas cambiar tu dominio a un dominio compatible. También te puedes contactar con tu proveedor DNS para ver si ofrece servicios de reenvío para los nombres de dominio.

Asegúrate de que en tu sitio no ocurra lo siguiente:
- Uso de más de un dominio apex. Por ejemplo, `example.com` y `anotherexample.com`.
- Uso de más de un subdominio de `www`. Por ejemplo, `www.example.com` y `www.anotherexample.com`.
- Uso de un dominio apex y de un subdominio personalizado. Por ejemplo, `example.com` y `docs.example.com`.

  La única excepción es el subdominio `www`. Si se configura correctamente, el subdominio `www` se redirigirá automáticamente al dominio de vértice. Para obtener más información, consulte "[Administración de un dominio personalizado para el sitio de {% data variables.product.prodname_pages %}](/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)".

{% data reusables.pages.wildcard-dns-warning %}

Para obtener una lista de dominios personalizados admitidos, consulte "[Acerca de dominios personalizados y {% data variables.product.prodname_pages %}](/articles/about-custom-domains-and-github-pages/#supported-custom-domains)".

## Errores HTTPS

Los sitios de {% data variables.product.prodname_pages %} que usan dominios personalizados configurados correctamente con registros DNS `CNAME`, `ALIAS`, `ANAME` o `A` son accesibles mediante HTTPS. Para más información, vea "[Protección del sitio de {% data variables.product.prodname_pages %} con HTTPS](/articles/securing-your-github-pages-site-with-https)".

Puede tardar hasta una hora que tu sitio se vuelva disponible a través de HTTPS una vez que configures tu dominio personalizado. Después de actualizar los ajustes DNS existentes, puede que debas eliminar y volver a agregar tu dominio personalizado a tu repositorio del sitio para activar el proceso de habilitación HTTPS. Para obtener más información, consulte "[Administración de un dominio personalizado para el sitio de {% data variables.product.prodname_pages %}](/articles/managing-a-custom-domain-for-your-github-pages-site)".

Si está usando registros de Autorización de entidad de certificación (CAA), debe existir al menos un registro de CAA con el valor `letsencrypt.org` para que el sitio sea accesible mediante HTTPS. Para obtener más información, consulte "[Autorización de entidad de certificación (CAA)](https://letsencrypt.org/docs/caa/)" en la documentación de Let's Encrypt.

## Formato de URL en Linux

Si la URL de tu sitio contiene un nombre de usuario o nombre de organización que comienza o termina con un guion, o que contiene guiones consecutivos, las personas que naveguen con Linux recibirán un error del servidor cuando traten de visitar tu sitio. Para corregir esto, cambia tu nombre de usuario de {% data variables.product.product_name %} y elimina cualquier caracter que no sea alfanumérico. Para obtener más información, consulte "[Cambio del nombre de usuario de {% data variables.product.prodname_dotcom %}](/articles/changing-your-github-username/)".

## Caché del navegador

Si has cambiado o eliminado recientemente tu dominio personalizado y no puedes acceder a la URL nueva en tu navegador, puede que debas limpiar el caché de tu navegador para llegar a la URL nueva. Para obtener más información acerca de limpiar tu caché, consulta la documentación de tu navegador.

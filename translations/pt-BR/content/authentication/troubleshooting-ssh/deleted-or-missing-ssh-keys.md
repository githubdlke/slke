---
title: Chaves SSH excluídas ou ausentes
intro: 'Como medida de segurança, o {% data variables.product.prodname_dotcom %} exclui automaticamente chaves SSH que não tenham sido usadas em um ano.'
redirect_from:
  - /articles/deleted-or-missing-ssh-keys
  - /github/authenticating-to-github/deleted-or-missing-ssh-keys
  - /github/authenticating-to-github/troubleshooting-ssh/deleted-or-missing-ssh-keys
versions:
  fpt: '*'
  ghec: '*'
topics:
  - SSH
shortTitle: Deleted or missing SSH keys
ms.openlocfilehash: aa26a5bf39db3f41aa3c3aa01f59c392a42f467f
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2022
ms.locfileid: '145083558'
---
O {% data variables.product.prodname_dotcom %} exclui automaticamente chaves SSH inativas para ajudar a manter as contas seguras, como depois que alguém deixa um emprego ou perde um computador.

Caso queira verificar se você ainda não usou uma chave SSH em um ano, revise o log de segurança da sua conta. Para obter mais informações, confira "[Como revisar o log de segurança](/articles/reviewing-your-security-log/)".

Depois que a chave SSH inativa for excluída, gere uma nova chave SSH e a associe à sua conta. Para obter mais informações, confira "[Como gerar uma nova chave SSH e adicioná-la ao ssh-agent](/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)" e "[Como adicionar uma nova chave SSH à sua conta do GitHub](/articles/adding-a-new-ssh-key-to-your-github-account/)".

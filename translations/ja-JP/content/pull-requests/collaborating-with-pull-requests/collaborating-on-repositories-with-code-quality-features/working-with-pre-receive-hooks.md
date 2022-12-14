---
title: Pre-receive フックを使って作業する
intro: '"*Pre-receive フック*" は、コミットがリポジトリにプッシュされる前に、コントリビューションに対するルールを強制します。'
redirect_from:
  - /github/collaborating-with-issues-and-pull-requests/collaborating-on-repositories-with-code-quality-features/working-with-pre-receive-hooks
  - /articles/working-with-pre-receive-hooks
  - /github/collaborating-with-issues-and-pull-requests/working-with-pre-receive-hooks
  - /github/collaborating-with-pull-requests/collaborating-on-repositories-with-code-quality-features/working-with-pre-receive-hooks
versions:
  ghes: '*'
shortTitle: Pre-receive hooks
ms.openlocfilehash: 6ca26aed9e9d92abfb6d742f7f4ca968c442b447
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2022
ms.locfileid: '146332593'
---
Pre-receive フックは、コントリビューションがリポジトリまたは Organization の方針を確実に満たすために、リポジトリにプッシュされたコードに対してテストを実行します。 コミット内容がテストに合格すると、プッシュはリポジトリに受け入れられます。 コミット内容がテストに合格しなかった場合、プッシュは受け入れられません。

プッシュが受け入れられない場合は、失敗した pre-receive フックに対応するエラーメッセージが表示されます。

```shell
$ git push
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 916 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
remote: always_reject.sh: failed with exit status 1
remote: error: rejecting all pushes
To https://54.204.174.51/hodor/nope.git
 ! [remote rejected] main -> main (pre-receive hook declined)
error: failed to push some refs to 'https://54.204.174.51/hodor/nope.git'
```

![失敗した pre-receive フックのエラーメッセージ](/assets/images/help/pull_requests/pre-receive-hook-failed-error.png)

{% data variables.product.product_name %} サイト管理者は、Organization またはリポジトリの pre-receive フックを作成および削除することができます。また、Organization またはリポジトリ管理者は、pre-receive フックを有効または無効にすることができます。 詳細については、[受信前フックを使用してポリシーを適用する](/enterprise/admin/guides/developer-workflow/using-pre-receive-hooks-to-enforce-policy)方法に関するページを参照してください。

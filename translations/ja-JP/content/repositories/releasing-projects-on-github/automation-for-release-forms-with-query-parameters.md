---
title: クエリパラメータ付きのリリースフォームのための自動化
intro: カスタマイズされた情報で新しいリリースフォームを自動的に展開することによってリリースを素早く作成するには、リリースフォームページの URL にクエリパラメータを追加できます。
redirect_from:
  - /articles/automation-for-release-forms-with-query-parameters
  - /github/administering-a-repository/automation-for-release-forms-with-query-parameters
  - /github/administering-a-repository/releasing-projects-on-github/automation-for-release-forms-with-query-parameters
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Repositories
shortTitle: Automate release forms
ms.openlocfilehash: 75c7fe4b79a6103060151742f1277861f23785c4
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2022
ms.locfileid: '145193564'
---
クエリパラメータはカスタマイズ可能な URL のオプション部分で、{% data variables.product.prodname_dotcom %} 上の検索フィルタの結果や Issue テンプレート、リリースフォームページといった特定の Web ページビューを共有できます。 独自のクエリパラメータを作成するには、キーと値のペアをマッチさせなければなりません。

クエリパラメータを使うには、同等のアクションを行うための適切な権限を持っていなければなりません。 たとえば事前にリリースフォームに記入しておくには、リリースを作成する権限を持っていなければなりません。 詳細については、「[リポジトリのリリースを管理する](/github/administering-a-repository/managing-releases-in-a-repository)」を参照してください。

クエリパラメータを使うのに不正なURLを作成したり、適切な権限を持っていなかったりした場合には、そのURLに対して404エラーページが返されます。  

## サポートされているクエリパラメータ

Query parameter (クエリ パラメーター) | 例
---  | ---
`tag` | `https://github.com/octo-org/octo-repo/releases/new?tag=v1.0.1` で "v1.0.1" という名前のタグに基づいてリリースが作成されます。
`target` | `https://github.com/octo-org/octo-repo/releases/new?target=release-1.0.1` で "release-1.0.1" ブランチへの最新のコミットに基づくリリースが作成されます。
`title` | `https://github.com/octo-org/octo-repo/releases/new?tag=v1.0.1&title=octo-1.0.1` で "v1.0.1" という名前のタグに基づいて "octo-1.0.1" という名前のリリースが作成されます。
`body` | `https://github.com/octo-org/octo-repo/releases/new?body=Adds+widgets+support` でリリース ボディに "Adds widget support" という説明を持つリリースが作成されます。
`prerelease` | `https://github.com/octo-org/octo-repo/releases/new?prerelease=1` で本番に備えができていないとされるリリースが作成されます。

## 参考資料

- [URL クエリからイシューを作成する](/issues/tracking-your-work-with-issues/creating-an-issue#creating-an-issue-from-a-url-query)
- [クエリ パラメーターを使って pull request を作成する](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/using-query-parameters-to-create-a-pull-request/)

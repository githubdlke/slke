---
title: 個人課題の作成
intro: コースにおいて、個人で修了するための課題を学生のために作成できます。
versions:
  fpt: '*'
permissions: 'Organization owners who are admins for a classroom can create and manage individual assignments for a classroom. {% data reusables.classroom.classroom-admins-link %}'
redirect_from:
  - /education/manage-coursework-with-github-classroom/creating-an-individual-assignment
  - /education/manage-coursework-with-github-classroom/create-an-individual-assignment
shortTitle: Individual assignment
ms.openlocfilehash: 4f5fab2f63ff686762a4fb6ccd5964b7f4d9cb3c
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2022
ms.locfileid: '147573869'
---
## 個人課題について

{% data reusables.classroom.assignments-individual-definition %}

{% data reusables.classroom.classroom-creates-individual-repositories %}

{% data reusables.classroom.about-assignments %}

個人課題の作成のビデオ デモについては、「[{% data variables.product.prodname_classroom %} のセットアップの基本](/education/manage-coursework-with-github-classroom/basics-of-setting-up-github-classroom)」をご覧ください。

{% data reusables.classroom.reuse-assignment-link %}

## 前提条件

{% data reusables.classroom.assignments-classroom-prerequisite %}

## 課題を作成する

{% data reusables.classroom.assignments-guide-create-the-assignment %}

## 課題の基本情報をセットアップする

課題に名前を付け、期限を設定するかを決定し、課題リポジトリの可視性を選択します。

- [課題に名前を付ける](#naming-an-assignment)
- [課題に期限を設定する](#assigning-a-deadline-for-an-assignment)
- [課題のタイプを選択する](#choosing-an-assignment-type)
- [課題リポジトリの可視性を選択する](#choosing-a-visibility-for-assignment-repositories)

### 課題に名前を付ける

個人課題では、{% data variables.product.prodname_classroom %}はリポジトリのプレフィックスと学生の{% data variables.product.product_name %}ユーザ名から、リポジトリに名前を付けます。 デフォルトでは、リポジトリのプレフィックスが課題のタイトルとなります。 たとえば、課題に "assignment-1" という名前を付け、{% data variables.product.product_name %} での学生のユーザー名が @octocat である場合、@octocat の課題リポジトリの名前は `assignment-1-octocat` になります。

{% data reusables.classroom.assignments-type-a-title %}

### 課題に期限を設定する

{% data reusables.classroom.assignments-guide-assign-a-deadline %}

### 課題のタイプを選択する

[Individual or group assignment]\(個人またはグループの課題\) の下のドロップダウン メニューを選んで、 **[Individual assignment]\(個人課題\)** をクリックします。 課題の作成後は、課題タイプを変更できません。 グループ課題を作成する場合は、「[グループ課題の作成](/education/manage-coursework-with-github-classroom/create-a-group-assignment)」をご覧ください。

### 課題リポジトリの可視性を選択する

{% data reusables.classroom.assignments-guide-choose-visibility %}

{% data reusables.classroom.assignments-guide-click-continue-after-basics %}

## スターターコードを追加し、開発環境を構成する

{% data reusables.classroom.assignments-guide-intro-for-environment %}

- [テンプレートリポジトリを作成する](#choosing-a-template-repository)
- [統合開発環境 (IDE) を選択する](#choosing-an-integrated-development-environment-ide)

### テンプレートリポジトリを作成する

デフォルトでは、新しい課題ではクラスルームの名簿に掲載されている各学生に対し、空のリポジトリが作成されます。 {% data reusables.classroom.you-can-choose-a-template-repository %}

{% data reusables.classroom.assignments-guide-choose-template-repository %}

{% data reusables.classroom.assignments-guide-click-continue-after-starter-code-and-feedback %}

### 統合開発環境 (IDE) を選択する

{% data reusables.classroom.about-online-ides %}詳細については、「[{% data variables.product.prodname_classroom %} と IDE の統合](/education/manage-coursework-with-github-classroom/integrate-github-classroom-with-an-ide)」を参照してください。

{% data reusables.classroom.classroom-codespaces-link %}

{% data reusables.classroom.assignments-guide-choose-an-online-ide %}

## 課題にフィードバックを行う

必要に応じて、課題を自動的に採点し、各提出物を学生と議論するための場を作成できます。

- [課題を自動的にテストする](#testing-assignments-automatically)
- [フィードバックのために pull request を作成する](#creating-a-pull-request-for-feedback)

### 課題を自動的にテストする

{% data reusables.classroom.assignments-guide-using-autograding %}

### フィードバックのためにプルリクエストを作成する

{% data reusables.classroom.you-can-create-a-pull-request-for-feedback %}

{% data reusables.classroom.assignments-guide-create-review-pull-request %}

{% data reusables.classroom.assignments-guide-click-create-assignment-button %}

## 学生を課題に招待する

{% data reusables.classroom.assignments-guide-invite-students-to-assignment %}

課題の **[クラスルームの名簿]** タブで、学生がクラスルームに参加して課題を受け取ったか、または提出したかを確認できます。 このタブでは、学生の {% data variables.product.prodname_dotcom %} エイリアスを関連する名簿識別子にリンクしたり、その逆にリンクしたりすることもできます。{% data reusables.classroom.assignments-to-prevent-submission %}

<div class="procedural-image-wrapper">
  <img alt="Individual assignment" class="procedural-image-wrapper" src="/assets/images/help/classroom/assignment-individual-hero.png">
</div>

## 学生の進捗状況を監視する
課題の概要ページには、課題の受け入れと学生の進捗状況の概要が表示されます。 課題の構成に基づいて、表示される概要情報が異なる場合があります。

- **[名簿に登録された学生]** : Classroom の名簿に登録されている学生の数。
- **[Added students]\(追加された学生\)** : 課題を受け入れていて、名簿識別子に関連付けられていない {% data variables.product.prodname_dotcom %} アカウントの数。
-  **[Accepted students]\(受け入れた学生\)** : この課題を受け入れたアカウントの数。
-  **[Assignment submissions]\(課題の提出\)** : 課題を提出した学生の数。 提出は、課題の期限にトリガーされます。
-  **[Passing students]\(合格した学生\)** : 現在、この課題の自動採点テストに合格している学生の数。

## 次の手順

- 課題を作成した後、学生はGitおよび{% data variables.product.product_name %}の機能を使用して課題を開始できます。 学生はリポジトリのクローン、コミットのプッシュ、ブランチの管理、プルリクエストの作成およびレビュー、マージコンフリクトへの対処、およびIssueの変更に関するディスカッションが可能です。 あなたも学生も、リポジトリのコミット履歴をレビューできます。 詳しくは、[{% data variables.product.prodname_dotcom %} の概要](/github/getting-started-with-github)、[リポジトリ](/repositories)、[issue と pull request での共同作業](/github/collaborating-with-issues-and-pull-requests)に関する記事をご覧ください。

- 課題を完了した学生がいる場合には、その学生のリポジトリにあるファイルをレビューできます。また、学生の作業についてをより深く理解するため、リポジトリの履歴や視覚化されたデータを確認できます。 詳細については、[グラフを使用したリポジトリ データの視覚化](/github/visualizing-repository-data-with-graphs)に関する記事を参照してください。

- プルリクエストの内の個々のコミットや行にコメントすることで、課題にフィードバックを行うことができます。 詳細については、「[pull request へコメントする](/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/commenting-on-a-pull-request)」および[コードから issue を開く方法](/github/managing-your-work-on-github/opening-an-issue-from-code)に関する記事を参照してください。 返信テンプレートを作成して一般的なエラーに関するフィードバックを提供する方法の詳細については、「[返信テンプレートについて](/github/writing-on-github/about-saved-replies)」を参照してください。

## 参考資料

- 「[教師向け {% data variables.product.prodname_global_campus %}](/education/explore-the-benefits-of-teaching-and-learning-with-github-education/github-global-campus-for-teachers)」
- [学習管理システムを {% data variables.product.prodname_classroom %} に接続する](/education/manage-coursework-with-github-classroom/connect-a-learning-management-system-to-github-classroom)

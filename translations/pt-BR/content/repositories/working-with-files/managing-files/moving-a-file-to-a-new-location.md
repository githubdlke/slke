---
title: Movendo um arquivo para um novo local
intro: 'Você pode transferir um arquivo para um diretório diferente em {% data variables.product.product_name %} ou usando a linha de comando.'
redirect_from:
  - /articles/moving-a-file-to-a-new-location
  - /github/managing-files-in-a-repository/moving-a-file-to-a-new-location
  - /articles/moving-a-file-to-a-new-location-using-the-command-line
  - /github/managing-files-in-a-repository/moving-a-file-to-a-new-location-using-the-command-line
  - /github/managing-files-in-a-repository/managing-files-on-github/moving-a-file-to-a-new-location
  - /github/managing-files-in-a-repository/managing-files-using-the-command-line/moving-a-file-to-a-new-location-using-the-command-line
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Repositories
shortTitle: Move a file
ms.openlocfilehash: 90e9434401795b6222d6304464c5a7d3839e0b7f
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2022
ms.locfileid: '145126975'
---
Além de alterar o local do arquivo, você também pode [atualizar o conteúdo do arquivo](/articles/editing-files-in-your-repository) ou [dar a ele um novo nome](/articles/renaming-a-file) no mesmo commit.

## Transferindo um arquivo para um novo local em {% data variables.product.product_name %}

{% tip %}

**Dicas**:

- Se você tentar mover um arquivo em um repositório ao qual não tem acesso, criaremos um fork do projeto na sua conta pessoal e ajudaremos você a enviar [uma solicitação de pull](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) para o repositório original após o commit da alteração.
- Alguns arquivos, como imagens, exigem que você os mova com a linha de comando. Para obter mais informações, confira "[Como mover um arquivo para um novo local usando a linha de comando](/articles/moving-a-file-to-a-new-location-using-the-command-line)".
- {% data reusables.repositories.protected-branches-block-web-edits-uploads %}

{% endtip %}

1. No repositório, navegue até o arquivo que deseja mover.
2. No canto superior direito da exibição de arquivo, clique em {% octicon "pencil" aria-label="The edit icon" %} para abrir o editor de arquivos.
![Ícone Editar arquivo](/assets/images/help/repository/move-file-edit-file-icon.png)
3. No campo de nome do arquivo, altere o nome do arquivo usando estas diretrizes: ![Como editar um nome de arquivo](/assets/images/help/repository/moving_files.gif)
    - Para mover o arquivo **para uma subpasta**, digite o nome da pasta desejada, seguido de `/`. Sua nova pasta é um novo item na navegação estrutural.
    - Para mover o arquivo para um diretório **acima do local atual do arquivo**, posicione o cursor no início do campo de nome do arquivo e digite `../` para subir um nível de diretório completo ou digite a chave `backspace` para editar o nome da pasta pai.
{% data reusables.files.write_commit_message %} {% data reusables.files.choose_commit_branch %} {% data reusables.files.propose_file_change %}

## Mover um arquivo para um novo local usando a linha de comando 

Você pode usar a linha de comando para mover arquivos dentro de um repositório, removendo o arquivo do local antigo e adicionando-o ao novo local.

Muitos arquivos podem ser [movidos diretamente no {% data variables.product.product_name %}](/articles/moving-a-file-to-a-new-location), mas alguns arquivos, como imagens, exigem que você os mova por meio da linha de comando.

{% data reusables.command_line.manipulating_file_prereqs %}

1. No seu computador, mova o arquivo para a nova localização dentro do diretório que foi criado localmente em seu computador quando você clonou o repositório.
{% data reusables.command_line.open_the_multi_os_terminal %}
3. Use `git status` para verificar os locais de arquivo antigos e novos.
  ```shell
  $ git status
  > # On branch <em>your-branch</em>
  > # Changes not staged for commit:
  > #   (use "git add/rm <file>..." to update what will be committed)
  > #   (use "git checkout -- <file>..." to discard changes in working directory)
  > #
  > #     deleted:    /<em>old-folder</em>/<em>image.png</em>
  > #
  > # Untracked files:
  > #   (use "git add <file>..." to include in what will be committed)
  > #
  > #     /<em>new-folder</em>/<em>image.png</em>
  > #
  > # no changes added to commit (use "git add" and/or "git commit -a")
  ```
{% data reusables.git.stage_for_commit %} Isso excluirá, ou `git rm`, o arquivo do local antigo e adicionará, ou `git add`, o arquivo ao novo local.
  ```shell
  $ git add .
  # Adds the file to your local repository and stages it for commit.
  # {% data reusables.git.unstage-codeblock %}
  ```
5. Use `git status` para verificar as alterações preparadas para o commit.
  ```shell
  $ git status
  > # On branch <em>your-branch</em>
  > # Changes to be committed:
  > #   (use "git reset HEAD <file>..." to unstage)
  > #
  > #    renamed:    /old-folder/image.png -> /new-folder/image.png
  # Displays the changes staged for commit
  ```
{% data reusables.git.commit-file %}
  ```shell
  $ git commit -m "Move file to new directory"
  # Commits the tracked changes and prepares them to be pushed to a remote repository.
  # {% data reusables.git.reset-head-to-previous-commit-codeblock %}
  ```
{% data reusables.git.git-push %}

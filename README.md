# Git/GitHub 共同開発演習

## 共有リポジトリモデル

---

# 1. 演習概要

本演習では、GitHubの**共有リポジトリモデル（Shared Repository Model）**を使用し、2人で共同開発を行った。

共有リポジトリモデルでは、リード役がGitHub上にリポジトリを作成し、開発者をCollaboratorとして追加する。

開発者は共有リポジトリをcloneし、自分の作業ブランチ上で開発を行う。

作業した内容を共有リポジトリへPushした後、Pull Request（PR）を作成してリード役にレビューを依頼する。

リード役がPull Requestをレビューし、問題がなければ`main`ブランチへMergeする。

今回の演習では、GitHubのWebブラウザとVisual Studio Code（VS Code）のGUI機能を使用して作業を行った。

---

# 2. チーム構成

今回のチームは2人で構成した。

| 担当 | 役割           |
| -- | ------------ |
| A  | リード役・リポジトリ管理 |
| B  | 開発者          |

AがGitHub上に共有リポジトリを作成し、BをCollaboratorとして追加する。

BはAの共有リポジトリをcloneし、自分の作業ブランチで開発を行う。

```text
A
│
│ リポジトリ作成
↓
共有リポジトリ
│
│ CollaboratorとしてBを追加
↓
B
│
│ clone
↓
Bのローカル環境
```

---

# 3. 共有リポジトリモデルとは

共有リポジトリモデルとは、**複数の開発者が1つの共有リポジトリを使用して開発を行う方式**である。

リポジトリの管理者が開発者をCollaboratorとして追加することで、開発者も共有リポジトリへPushできるようになる。

今回の演習では、Aがリポジトリの管理者となり、BをCollaboratorとして追加した。

BはAの共有リポジトリをcloneし、作業ブランチを作成して開発を行う。

変更内容は共有リポジトリへPushした後、Pull Requestを作成してAにレビューを依頼する。

```text
                    A
                リード役
                    │
                    ↓
             共有リポジトリ
                    │
              Collaborator
                    ↓
                    B
                開発者
                    │
                  clone
                    ↓
               ローカル環境
                    │
              作業ブランチ
                    │
                  編集
                    │
                 Commit
                    │
                  Push
                    ↓
             共有リポジトリ
                    │
                   PR
                    ↓
               AがReview
                    │
                  Merge
                    ↓
                  main
```

---

## フォークとプルモデルとの違い

### 共有リポジトリモデル

```text
B
│
│ Push
↓
共有リポジトリ
│
↓
Pull Request
│
↓
Aがレビュー
│
↓
main
```

### フォークとプルモデル

```text
B
│
│ Push
↓
B自身のFork
│
↓
Pull Request
│
↓
Aの元リポジトリ
│
↓
main
```

共有リポジトリモデルでは、**BがCollaboratorとして権限を与えられているため、Aの共有リポジトリへPushできる**点が特徴である。

一方、フォークとプルモデルでは、BはAの元リポジトリではなく、自分自身のForkへPushする。

---

# 4. 使用した環境

今回の演習では以下の環境を使用した。

* GitHub
* Visual Studio Code（VS Code）
* Webブラウザ

### GitHubで行った操作

* リポジトリ作成
* Collaborator追加
* Pull Request作成
* Pull Request確認
* Pull Requestレビュー
* Merge

### VS Codeで行った操作

* リポジトリ取得（Clone）
* ブランチ作成・切り替え
* ファイル編集
* ファイル追加
* Commit
* Push
* Pull

---

# 5. AがGitHub上にリモートリポジトリを作成

最初にAがGitHub上で演習用のリポジトリを作成した。

このリポジトリを、今回の共同開発で使用する**共有リポジトリ**とする。

```text
AのGitHubアカウント
        │
        ↓
   リポジトリ作成
        │
        ↓
  共有リポジトリ
```

【GitHubのリポジトリ作成画面】

<img width="800" alt="GitHubのリポジトリ作成画面" src="ここに画像URL">

---

# 6. AがBをCollaboratorとして追加

Aは作成したリポジトリの設定から、BをCollaboratorとして追加する。

GitHubのリポジトリ画面から、Collaboratorの設定を開き、BのGitHubアカウントを指定して招待する。

```text
A
│
↓
共有リポジトリ
│
│ Collaborator追加
↓
B
```

Bが招待を承認することで、Bも共有リポジトリを操作できるようになる。

【Collaborator追加画面】

<img width="800" alt="Collaborator追加画面" src="ここに画像URL">

---

# 7. Aがindex.htmlを作成

Aは`index.html`を作成し、以下の内容を記述した。

```html
Hello
```

作成した`index.html`を`main`ブランチへ追加してCommitする。

その後、GitHubへPushして、共有リポジトリの`main`ブランチへ`index.html`を登録する。

この時点での構成は以下の通りである。

```text
共有リポジトリ
└── main
    └── index.html
```

【index.htmlの画面】

<img width="800" alt="index.html" src="ここに画像URL">

---

# 8. BがリポジトリをClone

BはAから共有リポジトリへのCollaborator権限を付与された後、共有リポジトリをVS CodeへCloneする。

GitHubのリポジトリからURLを取得し、VS CodeのClone機能を使用してリポジトリを取得する。

```text
Aの共有リポジトリ
        │
        │ Clone
        ↓
Bのローカル環境
        │
        ↓
     VS Code
```

Clone後、BはVS Codeでリポジトリを開く。

【リポジトリのClone画面】

<img width="800" alt="リポジトリのClone" src="ここに画像URL">

---

# 9. Bが作業ブランチを作成

Bは`main`ブランチを元に作業ブランチを作成する。

```text
共有リポジトリ
│
├── main
│
└── work-branch-B
```

Bは`main`を直接編集せず、`work-branch-B`上で作業を行う。

【VS Codeのブランチ作成画面】

<img width="800" alt="ブランチ作成" src="ここに画像URL">

---

# 10. Bがindex.htmlを編集

BはVS Codeで`index.html`を編集する。

例えば、以下のように内容を変更する。

```html
Hello
World
```

変更後、VS Codeのソース管理画面から変更内容を確認する。

```text
ソース管理
└── 変更
    └── index.html
```

【VS Codeのソース管理画面】

<img width="800" alt="ソース管理" src="ここに画像URL">

---

# 11. BがCommit・Push

BはVS Codeのソース管理機能を使用して変更をCommitする。

その後、共有リポジトリへ作業ブランチをPushする。

```text
BのVS Code
     │
     │ Push
     ↓
共有リポジトリ
     │
     └── work-branch-B
```

共有リポジトリモデルでは、BにCollaborator権限があるため、Bが共有リポジトリへPushできる。

---

# 12. BがPull Requestを作成

BはGitHubのWebブラウザからPull Requestを作成する。

作業ブランチ`work-branch-B`から共有リポジトリの`main`ブランチへPull Requestを作成する。

```text
共有リポジトリ
work-branch-B
      │
      │ Pull Request
      ↓
共有リポジトリ
main
```

Pull Requestの作成時に、変更内容や確認してほしい内容を説明する。

【Pull Request作成画面】

<img width="800" alt="Pull Request作成画面" src="ここに画像URL">

---

# 13. AがBのPull Requestをレビュー・Merge

AはGitHubブラウザからBが作成したPull Requestを確認する。

変更された`index.html`を確認し、問題がないかレビューする。

問題がなければPull RequestをMergeし、共有リポジトリの`main`へ変更を取り込む。

```text
B
│
↓
work-branch-B
│
↓
Pull Request
│
↓
Aがレビュー
│
↓
Merge
│
↓
main
```

【Pull Requestレビュー画面】

<img width="800" alt="Pull Requestレビュー画面" src="ここに画像URL">

---

# 14. Aがローカルのmainを最新化

BのPull Requestが`main`へMergeされたため、Aはローカルの`main`を最新状態にする。

まずVS Codeで`main`ブランチへ切り替える。

その後、Pullを実行してGitHub上の最新の変更を取得する。

```text
共有リポジトリ
      │
      │ Pull
      ↓
AのVS Code
      │
      ↓
最新のmain
```

これにより、Bが行った変更がAのローカル環境にも反映される。

---

# 15. Aが作業ブランチを作成

Aは最新化した`main`を元に、新しい作業ブランチを作成する。

```text
共有リポジトリ
│
├── main
│
└── work-branch-A
```

Aも`main`を直接編集せず、作業ブランチ上で作業を行う。

---

# 16. Aがindex.htmlを編集

AはVS Codeで`index.html`を編集する。

例えば、Bの変更を残した状態でさらに内容を追加する。

```html
Hello
World
GitHub
```

編集後、変更内容を確認する。

---

# 17. AがCommit・Push

AはVS Codeのソース管理機能を使用して変更をCommitする。

その後、共有リポジトリへ作業ブランチをPushする。

```text
AのVS Code
     │
     │ Push
     ↓
共有リポジトリ
     │
     └── work-branch-A
```

---

# 18. AがPull Requestを作成・Merge

Aは自分の作業ブランチから`main`へのPull Requestを作成する。

```text
work-branch-A
      │
      ↓
Pull Request
      │
      ↓
main
```

変更内容を確認した後、問題がなければPull RequestをMergeする。

```text
work-branch-A
      │
      ↓
Pull Request
      │
      ↓
レビュー
      │
      ↓
Merge
      │
      ↓
main
```

【AのPull Request画面】

<img width="800" alt="AのPull Request" src="ここに画像URL">

---

# 19. Bがローカルのmainを最新化

Aの変更が`main`へMergeされたため、Bはローカルの`main`を最新化する。

まずVS Codeで`main`ブランチへ切り替える。

その後、Pullを実行する。

```text
共有リポジトリ
      │
      │ Pull
      ↓
BのVS Code
      │
      ↓
最新のmain
```

これにより、Aが行った変更がBのローカル環境にも反映される。

---

# 20. Bが作業ブランチを作成

Bは最新化した`main`を元に、新しい作業ブランチを作成する。

```text
共有リポジトリ
│
├── main
│
└── work-branch-B-css
```

Bはこの作業ブランチ上で`stylesheet.css`を追加する。

---

# 21. Bがstylesheet.cssを追加

BはVS Codeで`stylesheet.css`を新しく作成する。

例えば、以下のようなCSSを記述する。

```css
body {
    font-family: sans-serif;
}
```

作成した`stylesheet.css`をソース管理画面で確認する。

```text
ソース管理
└── 変更
    └── stylesheet.css
```

【stylesheet.css作成画面】

<img width="800" alt="stylesheet.css" src="ここに画像URL">

---

# 22. BがCommit・Push

Bは`stylesheet.css`をCommitする。

その後、共有リポジトリへPushする。

```text
BのVS Code
     │
     │ Push
     ↓
共有リポジトリ
     │
     └── work-branch-B-css
```

---

# 23. BがPull Requestを作成

BはGitHubブラウザから、`work-branch-B-css`から共有リポジトリの`main`へのPull Requestを作成する。

```text
work-branch-B-css
        │
        ↓
Pull Request
        │
        ↓
共有リポジトリ
        │
        ↓
      main
```

【BのPull Request作成画面】

<img width="800" alt="Pull Request作成画面" src="ここに画像URL">

---

# 24. AがBのPull Requestをレビュー・Merge

AはGitHubブラウザからBのPull Requestを確認する。

`stylesheet.css`の内容を確認し、問題がないことを確認する。

その後、Pull Requestを承認して共有リポジトリの`main`へMergeする。

```text
B
│
↓
work-branch-B-css
│
↓
Pull Request
│
↓
Aがレビュー
│
↓
Merge
│
↓
main
```

【Merge画面】

<img width="800" alt="Merge画面" src="ここに画像URL">

これで指定された一連の演習が完了した。

---

# 25. 今回の作業全体

今回の2人での共有リポジトリモデルによる作業をまとめると、以下のようになる。

```text
                         A
                    リード役
                       │
                       ↓
                 リポジトリ作成
                       │
                       ↓
                 共有リポジトリ
                       │
                       ↓
                 index.html作成
                       │
                       ↓
                      main
                       │
                       ↓
               BをCollaborator追加
                       │
                       ↓
                       B
                    開発者
                       │
                     Clone
                       │
                       ↓
                      main
                       │
                       ↓
                作業ブランチ作成
                       │
                       ↓
                index.html編集
                       │
                       ↓
                    Commit
                       │
                       ↓
                     Push
                       │
                       ↓
                      PR
                       │
                       ↓
                 Aがレビュー
                       │
                       ↓
                    Merge
                       │
                       ↓
                     main
                       │
                       ↓
                   AがPull
                       │
                       ↓
                作業ブランチ作成
                       │
                       ↓
                index.html編集
                       │
                       ↓
                    Commit
                       │
                       ↓
                     Push
                       │
                       ↓
                      PR
                       │
                       ↓
                    Merge
                       │
                       ↓
                     main
                       │
                       ↓
                   BがPull
                       │
                       ↓
                作業ブランチ作成
                       │
                       ↓
             stylesheet.css追加
                       │
                       ↓
                    Commit
                       │
                       ↓
                     Push
                       │
                       ↓
                      PR
                       │
                       ↓
                 Aがレビュー
                       │
                       ↓
                    Merge
                       │
                       ↓
                     main
```

---

# 26. 共有リポジトリモデルの基本的な流れ

今回の演習では、以下の流れで共同開発を行った。

```text
リポジトリ作成
      ↓
Collaborator追加
      ↓
リポジトリClone
      ↓
作業ブランチ作成
      ↓
ファイル編集
      ↓
Commit
      ↓
共有リポジトリへPush
      ↓
Pull Request
      ↓
リード役がレビュー
      ↓
Merge
      ↓
main
      ↓
Pullして最新化
      ↓
次の作業ブランチ作成
```

---

# 27. GitHubとVS Codeの役割

今回の演習では、GitHubとVS Codeを以下のように使い分けた。

| 操作             | 使用した環境  |
| -------------- | ------- |
| リポジトリ作成        | GitHub  |
| Collaborator追加 | GitHub  |
| リポジトリ取得（Clone） | VS Code |
| ブランチ作成         | VS Code |
| ブランチ切り替え       | VS Code |
| ファイル編集         | VS Code |
| ファイル追加         | VS Code |
| 変更確認           | VS Code |
| Commit         | VS Code |
| Push           | VS Code |
| Pull           | VS Code |
| Pull Request作成 | GitHub  |
| Pull Request確認 | GitHub  |
| コードレビュー        | GitHub  |
| Merge          | GitHub  |

---

# 28. Git Graphによる履歴確認

今回の演習では、複数の作業ブランチを作成し、それぞれからPull Requestを作成して`main`へ変更を取り込んだ。

Git Graphを確認すると、作業ブランチが作成され、Pull RequestによるMergeが行われた履歴を確認できる。

【ここに実際のGit Graphのスクリーンショットを貼る】

<img width="800" alt="Git Graph" src="ここに画像URL">

Git Graphには、例えば以下のようなMerge履歴が表示されている。

```text
Merge pull request
        ↓
      main
        ↑
       PR
        ↑
   作業ブランチ
```

この履歴から、作業ブランチで変更を行い、Pull Requestを経由して`main`へ変更を取り込んだことが確認できる。

---

# 29. スクリーンショット

実際の演習で使用した画面を以下に掲載する。

## GitHub

### ① 共有リポジトリ

【GitHubの共有リポジトリ画面】

<img width="800" alt="共有リポジトリ" src="ここに画像URL">

### ② Collaborator追加

【Collaborator追加画面】

<img width="800" alt="Collaborator追加" src="ここに画像URL">

### ③ Pull Request

【Pull Request作成画面】

<img width="800" alt="Pull Request" src="ここに画像URL">

### ④ Pull Requestレビュー

【レビュー画面】

<img width="800" alt="Pull Requestレビュー" src="ここに画像URL">

### ⑤ Merge

【Merge画面】

<img width="800" alt="Merge" src="ここに画像URL">

---

## Visual Studio Code

### ⑥ リポジトリClone

【VS CodeのClone画面】

<img width="800" alt="Clone" src="ここに画像URL">

### ⑦ ブランチ作成

【VS Codeのブランチ操作画面】

<img width="800" alt="ブランチ作成" src="ここに画像URL">

### ⑧ ソース管理

【VS Codeのソース管理画面】

<img width="800" alt="ソース管理" src="ここに画像URL">

### ⑨ Commit

【Commit時の画面】

<img width="800" alt="Commit" src="ここに画像URL">

### ⑩ Push / Pull

【VS Codeの同期操作画面】

<img width="800" alt="Push Pull" src="ここに画像URL">

### ⑪ Git Graph

【Git Graphのスクリーンショット】

<img width="800" alt="Git Graph" src="ここに画像URL">

---

# 30. まとめ

今回の演習では、A・Bの2人で**共有リポジトリモデル**による共同開発を行った。

AがGitHub上にリポジトリを作成し、BをCollaboratorとして追加した。

Bは共有リポジトリをCloneし、作業ブランチを作成して開発を行った。

Bは作業ブランチで`index.html`を編集し、共有リポジトリへPushした後、Pull Requestを作成した。

AはPull Requestの内容をレビューし、問題がなければ共有リポジトリの`main`へMergeした。

その後、Aはローカルの`main`を最新化して作業ブランチを作成し、`index.html`を編集してPull Requestを作成・Mergeした。

最後にBがローカルの`main`を最新化し、作業ブランチを作成して`stylesheet.css`を追加した。

BがPull Requestを作成し、Aがレビュー・Mergeすることで、指定された一連の演習が完了した。

今回の演習で行った基本的な流れは以下の通りである。

```text
Collaborator追加
      ↓
Clone
      ↓
作業ブランチ作成
      ↓
ファイル編集
      ↓
Commit
      ↓
共有リポジトリへPush
      ↓
Pull Request
      ↓
レビュー
      ↓
Merge
      ↓
main
```

また、共有リポジトリモデルでは、**開発者が同じリポジトリを共有し、Collaboratorとして権限を与えられた開発者がそのリポジトリへPushできる**ことが特徴である。

この演習を通して、GitHubのリポジトリ管理、ブランチ作成、Commit、Push、Pull、Pull Request、レビュー、Mergeという一連の共同開発の流れを実践した。

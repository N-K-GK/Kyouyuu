# Git/GitHub 共同開発演習

## 共有リポジトリモデル

---

# 1. 演習概要

本演習では、GitHubの**共有リポジトリモデル（Shared Repository Model）**を使用し、3人で共同開発を行った。

共有リポジトリモデルでは、リード役がGitHub上にリポジトリを作成し、開発者をCollaboratorとして追加する。

開発者は共有リポジトリをCloneし、自分の作業ブランチ上で開発を行う。

作業した内容を共有リポジトリへPushした後、Pull Request（PR）を作成してリード役にレビューを依頼する。

リード役がPull Requestをレビューし、問題がなければ`main`ブランチへMergeする。

今回の演習では、GitHubのWebブラウザとVisual Studio Code（VS Code）のGUI機能を使用して作業を行った。

---

# 2. チーム構成

今回のチームは3人で構成した。

| 担当 | 役割           |
| -- | ------------ |
| A  | リード役・リポジトリ管理 |
| B  | 開発者1         |
| C  | 開発者2         |

AがGitHub上に共有リポジトリを作成し、BとCをCollaboratorとして追加する。

BとCはAの共有リポジトリをCloneし、それぞれの作業ブランチで開発を行う。

```text
                         A
                    リード役
                       │
                       ↓
                  共有リポジトリ
                  │           │
          Collaborator   Collaborator
                  ↓           ↓
                  B           C
               開発者1       開発者2
                  │           │
                Clone       Clone
                  ↓           ↓
              BのVS Code   CのVS Code
```

---

# 3. 共有リポジトリモデルとは

共有リポジトリモデルとは、**複数の開発者が1つの共有リポジトリを使用して開発を行う方式**である。

リポジトリの管理者が開発者をCollaboratorとして追加することで、開発者も共有リポジトリへPushできるようになる。

今回の演習では、Aがリポジトリの管理者となり、BとCをCollaboratorとして追加した。

BとCはAの共有リポジトリをCloneし、それぞれ作業ブランチを作成して開発を行う。

変更内容は共有リポジトリへPushした後、Pull Requestを作成してAにレビューを依頼する。

```text
                       A
                    リード役
                       │
                       ↓
                 共有リポジトリ
                 /           \
                /             \
               ↓               ↓
               B               C
            開発者1          開発者2
               │               │
          作業ブランチ      作業ブランチ
               │               │
             編集             編集
               │               │
            Commit          Commit
               │               │
             Push            Push
               │               │
               ↓               ↓
              PR              PR
               │               │
               └───────┬───────┘
                       ↓
                   AがReview
                       ↓
                     Merge
                       ↓
                     main
```

---

# 4. フォークとプルモデルとの違い

### 共有リポジトリモデル

```text
B ──────────┐
            │ Push
            ↓
      共有リポジトリ
            │
            ↓
            PR
            │
            ↓
       Aがレビュー
            │
            ↓
          main
```

Cも同様に共有リポジトリへPushする。

```text
C ──────────┐
            │ Push
            ↓
      共有リポジトリ
            │
            ↓
            PR
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

共有リポジトリモデルでは、**BやCがCollaboratorとして権限を与えられているため、Aの共有リポジトリへ直接Pushできる**点が特徴である。

一方、フォークとプルモデルでは、BやCは自分自身のForkへPushする。

---

# 5. 使用した環境

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

# 6. AがGitHub上にリモートリポジトリを作成

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

---

# 7. AがB・CをCollaboratorとして追加

Aは作成したリポジトリの設定から、BとCをCollaboratorとして追加する。

GitHubのリポジトリ画面からCollaboratorの設定を開き、それぞれのGitHubアカウントを指定して招待する。

```text
             A
             │
             ↓
       共有リポジトリ
         /       \
        /         \
       ↓           ↓
      B             C
```

BとCが招待を承認することで、2人とも共有リポジトリを操作できるようになる。

【Collaborator追加画面】

<img width="886" height="891" alt="image" src="https://github.com/user-attachments/assets/6c1b5049-7a77-4745-919f-e05c70d3905f" />


---

# 8. Aがindex.htmlを作成

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

<img width="886" height="949" alt="image" src="https://github.com/user-attachments/assets/6f501f48-ddf0-4bf6-a774-66b61d7e39f7" />


---

# 9. BがリポジトリをClone

BはAから共有リポジトリへのCollaborator権限を付与された後、共有リポジトリをVS CodeへCloneする。

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

---

# 10. CがリポジトリをClone

CもBと同様に、Aの共有リポジトリをVS CodeへCloneする。

```text
 Aの共有リポジトリ
        │
        │ Clone
        ↓
  Cのローカル環境
        │
        ↓
     VS Code
```

これにより、BとCのローカル環境に同じ`main`の内容が取得される。

```text
共有リポジトリ
      │
      ├────────→ BのVS Code
      │
      └────────→ CのVS Code
```

---

# 11. Bが作業ブランチを作成

Bは`main`ブランチを元に作業ブランチを作成する。

```text
Bのローカルリポジトリ
│
├── main
│
└── work-branch-B
```

Bは`main`を直接編集せず、`work-branch-B`上で作業を行う。

---

# 12. Bがindex.htmlを編集

BはVS Codeで`index.html`を編集する。

以下のように内容を変更する。

```html
Hello
B_編集
```

変更後、VS Codeのソース管理画面から変更内容を確認する。

```text
ソース管理
└── 変更
    └── index.html
```

---

# 13. BがCommit・Push

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

# 14. BがPull Requestを作成

BはGitHubのWebブラウザからPull Requestを作成する。

作業ブランチ`work-branch-B`から共有リポジトリの`main`ブランチへPull Requestを作成する。

```text
work-branch-B
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

---

# 15. AがBのPull Requestをレビュー・Merge

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

---

# 16. Cが作業ブランチを作成

Bの変更が`main`へMergeされた後、Cも最新の`main`を取得する。

Cはローカルの`main`をPullして最新化した後、作業ブランチを作成する。

```text
Cのローカルリポジトリ
│
├── main
│
└── work-branch-C
```

Cは`main`を直接編集せず、`work-branch-C`上で作業を行う。

---

# 17. Cがindex.htmlを編集

CはVS Codeで`index.html`を編集する。

Bの変更を残した状態でさらに内容を追加する。

```html
Hello
B_編集
Add Line C
```

編集後、変更内容を確認する。

---

# 18. CがCommit・Push

CはVS Codeのソース管理機能を使用して変更をCommitする。

その後、共有リポジトリへ作業ブランチをPushする。

```text
CのVS Code
     │
     │ Push
     ↓
共有リポジトリ
     │
     └── work-branch-C
```

---

# 19. CがPull Requestを作成

CはGitHubブラウザから、`work-branch-C`から共有リポジトリの`main`へのPull Requestを作成する。

```text
work-branch-C
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

---

# 20. AがCのPull Requestをレビュー・Merge

AはGitHubブラウザからCのPull Requestを確認する。

Cが変更した`index.html`の内容を確認し、問題がないことを確認する。

その後、Pull Requestを承認して共有リポジトリの`main`へMergeする。

```text
C
│
↓
work-branch-C
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

---

# 21. Aがローカルのmainを最新化

BとCのPull Requestが`main`へMergeされたため、Aはローカルの`main`を最新状態にする。

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

これにより、BとCが行った変更がAのローカル環境にも反映される。

---

# 22. Aが作業ブランチを作成

Aは最新化した`main`を元に、新しい作業ブランチを作成する。

```text
Aのローカルリポジトリ
│
├── main
│
└── work-branch-A
```

Aも`main`を直接編集せず、作業ブランチ上で作業を行う。

---

# 23. Aがindex.htmlを編集

AはVS Codeで`index.html`を編集する。

BとCの変更を残した状態でさらに内容を追加する。

```html
Hello
B_編集
Add Line C

A_branch
```

編集後、変更内容を確認する。

---

<img width="886" height="952" alt="image" src="https://github.com/user-attachments/assets/d414eaa9-2366-46ae-a4ab-d7217df7d86d" />


# 24. AがCommit・Push

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

# 25. AがPull Requestを作成・Merge

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

---

# 26. Bがローカルのmainを最新化

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

---

# 27. Bが作業ブランチを作成

Bは最新化した`main`を元に、新しい作業ブランチを作成する。

```text
Bのローカルリポジトリ
│
├── main
│
└── work-branch-B-css
```

Bはこの作業ブランチ上で`stylesheet.css`を追加する。

---

# 28. Bがstylesheet.cssを追加

BはVS Codeで`stylesheet.css`を新しく作成する。

作成した`stylesheet.css`をソース管理画面で確認する。

```text
ソース管理
└── 変更
    └── stylesheet.css
```

---

# 29. BがCommit・Push

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

# 30. BがPull Requestを作成

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

---

# 31. AがBのPull Requestをレビュー・Merge

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

<img width="886" height="919" alt="image" src="https://github.com/user-attachments/assets/318addd2-7417-42f7-a2e2-2d77b72ebc5a" />


---

# 32. Cがローカルのmainを最新化

Aの変更が`main`へMergeされたため、Cはローカルの`main`を最新化する。

まずVS Codeで`main`ブランチへ切り替える。

その後、Pullを実行する。

```text
共有リポジトリ
      │
      │ Pull
      ↓
 CのVS Code
      │
      ↓
 最新のmain
```

---

# 33. Cが作業ブランチを作成

Cは最新化した`main`を元に、新しい作業ブランチを作成する。

```text
Cのローカルリポジトリ
│
├── main
│
└── work-branch-C-css
```

Cはこの作業ブランチ上で`stylesheet.css`を追加する。

---

# 34. Bがstylesheet_c.cssを追加

BはVS Codeで`stylesheet_c.css`を新しく作成する。

作成した`stylesheet_c.css`をソース管理画面で確認する。

```text
ソース管理
└── 変更
    └── stylesheet_c.css
```

---

# 35. CがCommit・Push

Cは`stylesheet_c.css`をCommitする。

その後、共有リポジトリへPushする。

```text
CのVS Code
     │
     │ Push
     ↓
共有リポジトリ
     │
     └── work-branch-C-css
```

---

# 36. CがPull Requestを作成

CはGitHubブラウザから、`work-branch-C-css`から共有リポジトリの`main`へのPull Requestを作成する。

```text
work-branch-C-css
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

---

# 37. AがCのPull Requestをレビュー・Merge

AはGitHubブラウザからCのPull Requestを確認する。

`stylesheet_c.css`の内容を確認し、問題がないことを確認する。

その後、Pull Requestを承認して共有リポジトリの`main`へMergeする。

```text
C
│
↓
work-branch-C-css
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

<img width="886" height="919" alt="image" src="https://github.com/user-attachments/assets/318addd2-7417-42f7-a2e2-2d77b72ebc5a" />




これで指定された一連の演習が完了した。

---

# 38. 今回の作業全体

今回の3人での共有リポジトリモデルによる作業をまとめると、以下のようになる。

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
              ┌────────┴────────┐
              ↓                 ↓
              B                 C
           開発者1           開発者2
              │                 │
            Clone             Clone
              │                 │
              ↓                 ↓
             main              main
              │                 │
         ブランチ作成       ブランチ作成
              │                 │
        index.html編集     index.html編集
              │                 │
           Commit            Commit
              │                 │
            Push              Push
              │                 │
              ↓                 ↓
             PR                PR
              │                 │
              └────────┬────────┘
                       ↓
                   Aがレビュー
                       ↓
                     Merge
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
                       ↓
                    Merge
                       ↓
                     main
                       │
                       ↓
              ┌────────┴────────┐
              ↓                 ↓
              B                 C
           開発者1           開発者2
              │                 │
             Pull              Pull
              │                 │
              ↓                 ↓
             main              main
              │                 │
        作業ブランチ作成    作業ブランチ作成
              │                 │
      stylesheet.css追加   stylesheet_c.css追加
              │                 │
           Commit            Commit
              │                 │
            Push              Push
              │                 │
              ↓                 ↓
             PR                PR
              │                 │
              ↓                 ↓
            Merge             Merge
              │                 │
              └────────┬────────┘
                       ↓
                     main
```

---

# 39. 共有リポジトリモデルの基本的な流れ

今回の演習では、以下の流れで共同開発を行った。

```text
リポジトリ作成
      ↓
B・CをCollaboratorに追加
      ↓
 B・CがClone
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
  Aがレビュー
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

# 40. GitHubとVS Codeの役割

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

# 41. Git Graphによる履歴確認

今回の演習では、A・B・Cそれぞれが作業ブランチを作成し、Pull Requestを作成して`main`へ変更を取り込んだ。

Git Graphを確認すると、複数の作業ブランチが作成され、Pull RequestによるMergeが行われた履歴を確認できる。

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

# 42. スクリーンショット

実際の演習で使用した画面を以下に掲載する。

## GitHub

### ① Collaborator追加

【Collaborator追加画面】

<img width="886" height="891" alt="image" src="https://github.com/user-attachments/assets/4a370b1a-1868-435f-88bb-097438fed0a0" />


### ② Merge

【Merge画面】

<img width="886" height="919" alt="image" src="https://github.com/user-attachments/assets/d7965fe4-3c59-4ad2-bd91-67f9de40014e" />


---

## Visual Studio Code

### ③ ブランチ作成

【VS Codeのブランチ操作画面】

<img width="886" height="952" alt="image" src="https://github.com/user-attachments/assets/c3ac8cb5-aa62-4cb9-8fd2-35a471b2ffb4" />


### ④ ソース管理

【VS Codeのソース管理画面】

<img width="467" height="520" alt="image" src="https://github.com/user-attachments/assets/99d1a3bd-91dd-4098-9667-81e6df21f4ff" />


---

# 43. まとめ

今回の演習では、A・B・Cの3人で**共有リポジトリモデル**による共同開発を行った。

AがGitHub上にリポジトリを作成し、BとCをCollaboratorとして追加した。

BとCは共有リポジトリをCloneし、それぞれ作業ブランチを作成して開発を行った。

BとCは作業ブランチで変更を行い、共有リポジトリへPushした後、Pull Requestを作成した。

AはそれぞれのPull Requestの内容をレビューし、問題がなければ共有リポジトリの`main`へMergeした。

その後、Aはローカルの`main`を最新化して作業ブランチを作成し、`index.html`を編集してPull Requestを作成・Mergeした。

Bがローカルの`main`を最新化し、作業ブランチを作成して`stylesheet.css`を追加した。

BがPull Requestを作成し、Aがレビュー・Mergeした。

最後にCがローカルの`main`を最新化し、作業ブランチを作成して`stylesheet_c.css`を追加した。

CがPull Requestを作成し、Aがレビュー・Mergeすることで、指定された一連の演習が完了した。

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

また、共有リポジトリモデルでは、**開発者ごとにForkを作成する必要がなく、同じ共有リポジトリを使用して共同開発を行う**ことが特徴である。

この演習を通して、GitHubのリポジトリ管理、Collaborator管理、ブランチ作成、Commit、Push、Pull、Pull Request、レビュー、Mergeという一連の共同開発の流れを実践した。

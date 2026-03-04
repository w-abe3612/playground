# playground

このリポジトリは、以下の3つの用途の開発環境を **Dockerコンテナで分離して管理**するためのものです。

1. CadQuery（CADモデリング）
2. AI学習（PyTorch / TensorFlow）
3. 自作オーディオブック生成

WindowsとMacの両方で **同じコンテナ環境を再現できる**ように構成しています。

---

# ディレクトリ構成


playground
├─ compose.yml
├─ README.md
│
├─ cadquery
│ ├─ Dockerfile
│ ├─ notebooks
│ └─ export
│
├─ ai
│ ├─ Dockerfile
│ ├─ notebooks
│ ├─ data
│ ├─ models
│ └─ outputs
│
└─ audiobook
├─ Dockerfile
├─ scripts
├─ input
└─ out


---

# 前提条件

## Windows

以下をインストールしてください。

- Docker Desktop
- WSL2（Docker Desktopインストール時に自動設定されることが多い）

確認コマンド

```bash
docker version
docker compose version

Serverが表示されればDockerは正常に動作しています。

Mac（Intel）

以下をインストールしてください。

Docker Desktop for Mac

確認コマンド

docker version
docker compose version
リポジトリの取得

Windows / Mac 共通

git clone https://github.com/w-abe3612/playground.git
cd playground
コンテナ起動

用途ごとに3つのコンテナがあります。

CadQuery環境

CadQuery開発用コンテナです。

Jupyter Notebookが起動します。

docker compose up --build cadquery-jupyter

ブラウザでアクセス

http://localhost:8888

停止

docker compose down
AI学習環境

AI学習用コンテナです。

docker compose up --build ai-jupyter

ブラウザ

http://localhost:8889

停止

docker compose down

GPUについて

Mac → GPU使用不可（CPUのみ）

Windows + NVIDIA GPU → 将来的にGPU対応予定

オーディオブック生成環境

このコンテナは 常駐しないツールコンテナです。

必要な時だけ実行します。

起動

docker compose run --rm audiobook-tools bash
VOICEVOX連携

自作オーディオブック生成では VOICEVOX ENGINE を使用します。

VOICEVOXは ホスト側で起動してください。

例

http://127.0.0.1:50021

Dockerコンテナからは以下でアクセスします。

http://host.docker.internal:50021

接続確認

docker compose run --rm audiobook-tools curl http://host.docker.internal:50021/version
よくあるトラブル
Docker Desktopが起動していない

Windowsで以下のエラーが出る場合

open //./pipe/dockerDesktopLinuxEngine

Docker Desktopが起動していない可能性があります。

Docker Desktopを起動し、以下を確認してください。

docker version
今後追加予定

このリポジトリは最小構成です。

今後追加予定

CadQuery

conda環境

cadquery

cq-editor GUI

AI

PyTorch

TensorFlow

GPU対応

Audiobook

VOICEVOX

テキスト分割

音声生成

mp3結合

開発方針

このリポジトリは

Windows

Mac

Linux

すべてで 同一のDocker環境を再現すること を目的としています。

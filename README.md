# PyTorch dockerの使用手順

[![Push to Docker registry](https://github.com/undefeated-davout/pytorch-docker/actions/workflows/custom_build.yml/badge.svg)](https://github.com/undefeated-davout/pytorch-docker/actions/workflows/custom_build.yml)

## Dockerビルド

```.bash
make -f docker.Makefile
```

## 起動

```.bash
docker-compose up -d
```

## JupyterNotebookにアクセス

```.bash
# ログを確認して
docker-compose logs -f

# 以下の形式のURLにアクセスしてJupyterNotebookを呼び出す
# http://127.0.0.1:8888/?token=xxxxxxxxxx
```

## コンテナログイン

```.bash
docker exec -it pytorch-docker.app /bin/bash --login
```

## 作業ディレクトリ

```.bash
./custom/workspace/
```

## カスタマイズ用のソース配置ディレクトリ

```.bash
./custom/
```

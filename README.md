## k8s-practice

[Kubernetes実践入門 プロダクションレディなコンテナ＆アプリケーションの作り方](https://gihyo.jp/book/2019/978-4-297-10438-2) を頑張ってハンズオンするリポジトリ

## ３章終了時点でのコマンドメモ

メモはコミットハッシュ 25e167b61230d843bf3e3f25e5433bbfec0c3843 時点でのもの

クラスタの削除(わけわかんなくなったら一旦削除が良い)

```bash
$ minikube delete
```

クラスタを開始

```bash
$ minikube start
```

順にapply(kc は kubectl の alias)

```bash
$ kc apply -f secret.yaml 
$ kc apply -f cm-file.yaml 
$ kc apply -f cm.yaml 
$ kc apply -f mysql-cm-backup.yaml 
$ kc apply -f mysql-cm-script.yaml 
$ kc apply -f mysql-pv.yaml 
$ kc apply -f mysql-pvc.yaml 
$ kc apply -f mysql-sts.yaml 
$ kc apply -f mysql-svc-read.yaml 
$ kc apply -f mysql-svc.yaml 
$ kc apply -f mattermost-deploy.yaml 
$ kc apply -f mattermost-service.yaml
$ kc apply -f mattermost-ingress.yaml
```

アプリケーションサービスへのアクセス (ingress はなんかだめだ)

```bash
$ minikube service mattermost
```

## たまに使うコマンドメモ

Docker イメージの更新してプッシュ

```bash
$ docker build -t sa2knight/mattermost:4.10.4 .
$ docker push sa2knight/mattermost:4.10.4
```
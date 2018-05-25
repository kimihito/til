+++
title = "HerokuでCloudflareを使う"
date = 2018-05-25T13:26:20+09:00
tags = ["Heroku", "Cloudflare", "pointDNS"]
draft =  false
+++

# HerokuでCloudflareを使う

## 経緯

- 個人で作っているサービスのコストを減らしたい。

- [【完全無料】Herokuで独自ドメイン + HTTPSに対応する【Rails】 - Qiita](https://qiita.com/serinuntius/items/f7f08b2221f5ad068f5d) を見つけたので試してみようと思った


## やったこと

1. pointDNSを使っていたのでアドオンを解除
2. Herokuの有料プランから無料へ
3. [Configure Cloudflare and Heroku over HTTPS – Cloudflare Support](https://support.cloudflare.com/hc/en-us/articles/205893698-Configure-Cloudflare-and-Heroku-over-HTTPS?flash_digest=a18f5b966ce0531d6fe47de9650efe940150dcb3) の通りに作業をする



## はまったこと

1 ~ 3 までの手順でやった上でアクセスしても動かなかったけど、ほっといたら動くようになっていた。

## 参考にしたサイト

- [Configure Cloudflare and Heroku over HTTPS – Cloudflare Support](https://support.cloudflare.com/hc/en-us/articles/205893698-Configure-Cloudflare-and-Heroku-over-HTTPS)
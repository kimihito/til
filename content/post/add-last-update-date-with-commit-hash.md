+++
date = "2017-09-30T15:08:11+09:00"
title =  "Hugoで記事に最終更新日とそのコミットを表示する"
tags =  ["Hugo", "wercker"]
draft = false
+++

最初に投稿したあとに、更新することもあるのでそのコミットログと、いつの更新だったかを把握できるようにしたかった。

すでにHugoには[Gitの情報を取得できる変数があった](https://gohugo.io/variables/git/)Gitの情報を取得できる変数があるのでそれを利用する。

有効にする方法は、 `config.toml` に

```toml
enableGitInfo = true
```

と書くと有効になります。

また、最終更新日の表示は、[Page Variables](https://gohugo.io/variables/page/#page-variables)の `.Lastmod` が利用できます。

今回その2つを利用して、

```html

{{ if (isset . .GitInfo)}}
  <h3 class="subtitle is-6">{{.Site.Params.latest }}</h3>
  <div class="content">
    <a href="{{.Site.Params.repourl}}/commit/{{.GitInfo.Hash}}">{{.Lastmod}}</a>
  </div>
{{ end }}
```

と書きました。(`.Site.Params.repourl`にはGitHubのURLを入れています)


## ハマったこと


### コミットのない投稿のプレビューができない

新しく作った投稿にはコミットハッシュがないため、`.GitInfo`が取得できないというエラーが出て`hugo server`を利用したプレビューが表示されません。

これを回避するために、`if (isset . .GitInfo)` を追加して、`.GitInfo`がある場合のみ表示するようにしました。

### wercker経由でのデプロイに失敗する

このサイトは、werckerを利用してGitHub Pages上にデプロイしています。

Hugoのビルドは、[`arjen/hugo-build`](https://github.com/ArjenSchwarz/wercker-step-hugo-build)を利用しています。

`.GitInfo` を利用するにあたって、`gitinfo.go:39: Got error reading Git log: Git executable not found in $PATH` という[エラーが出ていました](https://app.wercker.com/kimihito/til/runs/ci/59cdfc828e888f0001ad3626?step=59cdfc89af52880001c287f9)。

解決方法としては、

```yaml
  steps:
    - install-packages:
        packages: git
    - arjen/hugo-build:
        version: "0.18"
        theme: hemingway
        flags: --buildDrafts=true
```

というように、`arjen/hugo-build`を利用する前に`git`をインストールすることで対処できました。

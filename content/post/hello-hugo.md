+++
date = "2017-01-31T22:59:05+09:00"
title = "HugoをGitHub Pagesで動かす"
tags = ["Hugo", "GitHub Pages"]

+++

# 参考

[Hugo - Automated deployments with Wercker](https://gohugo.io/tutorials/automated-deployments/)

だいたいはここに従ったとおりにやった。

# 使用したテーマ

[tanksuzuki/hemingway: Really minimal blog theme for hugo.](https://github.com/tanksuzuki/hemingway)

h1 が \# として表示されたりしているのが好きなので選択した。

# ハマったところ

- テーマが `git init` に含まれてなかったので表示されなかった。

- [tanksuzuki/hemingway](https://github.com/tanksuzuki/hemingway) が Hugo 0.16から？じゃないと対応していないとの[ログが出た](https://app.wercker.com/kimihito/til/runs/build/5891d4f1371df80100b47052?step=5891d4f6e3159e00010dd552)ので、[バージョンをあげた](https://github.com/kimihito/til/commit/f062c5bbdf57c1043fecbc3516b9869e5f252f27)

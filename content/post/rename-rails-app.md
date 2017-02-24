+++
date = "2017-02-24T16:31:09+09:00"
title = "Railsのアプリをリネームしたい"
tags = ['Rails', 'Gem']

+++

[morshedalam/rename: To rename rails application](https://github.com/morshedalam/rename) をいれて、`bundle install`

その後

```
rails g rename:app_to 変えたい名前
```

で変わります。`Rails.application.config.session_store` も変わっちゃうっぽい。

なぜかREADMEだと上記のコマンドが書いてなかった。


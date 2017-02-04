+++
date = "2017-02-04T20:02:34+09:00"
title = "Minitestのインテグレーションテストでメールの送信テストをしたい"
tags = ["Rails", "Minitest"]

+++

## やりたいこと

Minitestを利用したインテグレーションテストでメールが送信されているかをテストしたかったが、動作していなかった。

## やったこと

`test/test_helper.rb` に以下を追加したところメールの動作テストができた

```
ActionMailer::Base.delivery_method = :test
```




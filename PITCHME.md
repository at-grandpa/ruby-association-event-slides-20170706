---?image=assets/images/crystal-logo.png&size=45% auto

---

- 資料は公開済みです
  - [https://gitpitch.com/at-grandpa/ruby-association-event-slides-20170706#](https://gitpitch.com/at-grandpa/ruby-association-event-slides-20170706#)
  - [@at_grandpa](https://twitter.com/at_grandpa)でつぶやきます
- 実況ツイートなど大歓迎です
- スライド中のリンクはクリックできます
  -  GitPitch便利

---

###### Matzさんの後で緊張しています🌀

---

## RubyKaigi 2016

<img src="assets/images/rubykaigi-2016-01.JPG" width="60%">

###### [#rubyfriends](https://twitter.com/hashtag/rubyfriends?src=hash)  [#rubykaigi](https://twitter.com/hashtag/rubykaigi?src=hash)


---

<img src="assets/images/blog-01-rubykaigi.png" width="60%">

###### [http://at-grandpa.hatenablog.jp/entry/2016/09/09/083547](http://at-grandpa.hatenablog.jp/entry/2016/09/09/083547)


---

## 🎉RubyKaigi 2017⛩

<img src="assets/images/rubykaigi-2017-01.png" width="60%">

###### [http://rubykaigi.org/2017](http://rubykaigi.org/2017)


---

<img src="assets/images/icon_512.jpg" width="30%">

- twitter: [@at_grandpa](https://twitter.com/at_grandpa)
- github: [@at-grandpa](https://github.com/at-grandpa)
###### 　
###### I love Crystal lang.


---

<img src="assets/images/blog-02-clim.png" width="70%">

###### [１秒でも早くCLIツールを作りたい by Crystal](http://at-grandpa.hatenablog.jp/entry/clim)


---

<img src="assets/images/blog-03-des.png" width="70%">

###### [ちょっとしたdocker環境を素早く作れるツールを作った](http://at-grandpa.hatenablog.jp/entry/2017/06/22/090935)


---

## Crystal-lang [Google Group](https://groups.google.com/forum/?fromgroups#!forum/crystal-lang)

<img src="assets/images/google-group-01-all.png" width="90%">


---

<img src="assets/images/google-group-02-lldb-question.png" width="70%">

###### lldbでローカル変数の値が見れないんだけど
###### どうしたらいい？


---

<img src="assets/images/google-group-03-answer.png" width="50%">

###### 「Hi, grandpa」=「やぁ、おじいちゃん」


---

## Crystal周りの活動

- たまにissue作ったり
- たまにPR作ったり
- ライブラリ書いたり
- 勉強会開いたり
- 技術書典２で頒布したり


---

## Crystal勉強会 #4 in 渋谷

<img src="assets/images/blog-04-study-crystal.png" width="80%">


---

## 技術書典２

<img src="assets/images/blog-05-techbookfest2.png" width="45%">


---

## 技術書典３ 開催決定 🎉

<img src="assets/images/techbookfest3.png" width="65%">


---?image=assets/images/crystal-web-site-top.png&size=cover

### Crystalのこれまでの歩みと
### v1.0 に向けたロードマップ
##### 2017.07.06 @at_grandpa


---

#### Crystalを
### ご存知の方🙋


---

### 触ったことある方🙋

+++

### ご清聴ありがとうございました🙇

---

### ライブラリを作ったことある方🙋

+++

### ご清聴ありがとうございました🙇

---

### Contributorの方🙋

+++

### ご清聴ありがとうございました🙇

---

### Crystalについて
### いろいろ調べてきました

---

### [Crystal 言語周辺の 2017年は？（妄想）](http://qiita.com/yahhonob/items/a24dee215c70425196d3)

<img src="assets/images/qiita-crystal-2017.png" width="55%">

###### author: [@yahhonob](https://twitter.com/yahhonob)さん

---

## Github Stars⭐

---

### 現時点では...
### [crystal-lang/crystal](https://github.com/crystal-lang/crystal)

---

### Star数の推移を追ってみます📈

---

### 便利なサイト
### [http://www.timqian.com/star-history/](http://www.timqian.com/star-history/)

---

<img src="assets/images/github-star-crystal.png" width="80%">

---

<img src="assets/images/github-star-crystal-elixir.png" width="80%">

---

<img src="assets/images/github-star-crystal-elixir-rust.png " width="80%">

---

<img src="assets/images/github-star-crystal-elixir-rust-go.png" width="80%">

---

<img src="assets/images/github-star-crystal-elixir-rust-go-swift.png" width="80%">

---

### ライブラリ

---

### shards

- rubyの`bundler`的存在
- `shards.yml`に設定記述
- githubのリポジトリ指定
  - branchやタグ指定可能
- `shards.lock`を生成

---

```
$ crystal init app kemal_test
      create  kemal_test/.gitignore
      create  kemal_test/.editorconfig
      create  kemal_test/LICENSE
      create  kemal_test/README.md
      create  kemal_test/.travis.yml
      create  kemal_test/shard.yml
      create  kemal_test/src/kemal_test.cr
      create  kemal_test/src/kemal_test/version.cr
      create  kemal_test/spec/spec_helper.cr
      create  kemal_test/spec/kemal_test_spec.cr
Initialized empty Git repository in /Users/y-tsuchida/crystal/test/kemal_test/.git/
$ cd kemal_test
$ vim shard.yml
$ cat shard.yml
name: kemal_test
version: 0.1.0

authors:
  - at-grandpa

targets:
  kemal_test:
    main: src/kemal_test.cr

crystal: 0.23.0

license: MIT

dependencies:
  kemal:
    github: kemalcr/kemal
    branch: master

$ shards install
Updating https://github.com/kemalcr/kemal.git
Updating https://github.com/luislavena/radix.git
Updating https://github.com/jeromegn/kilt.git
Installing kemal (master)
Installing radix (0.3.8)
Installing kilt (0.4.0)
$ vim src/kemal_test.cr
$ cat src/kemal_test.cr
require "./kemal_test/*"
require "kemal"

get "/" do
  "Hello World!"
end

Kemal.run

$ crystal run src/kemal_test.cr
[development] Kemal is ready to lead at http://0.0.0.0:3000
```
@[1](`Crystal init`コマンドで雛形を生成します)
@[2-12](雛形が生成されます)
@[13]()
@[14](`shads.yml`を編集します)
@[15]()
@[16-34]()
@[30-33](`kemal`を記述します)
@[35](依存ライブラリをinstallします)
@[36-41](installできました)
@[42](ソースコードを編集します)
@[43]()
@[44-50]()
@[45](`require`できます)
@[52-53](実行できます)


---

### 3枚目のスライド

```crystal
a = "a"
b = "b"
c = "c"
d = "d"
a = "a"
a = "a"
a = "a"
a = "a"
a = "a"
a = "a"
b = "b"
c = "c"
d = "d"
b = "b"
c = "c"
d = "d"
b = "b"
c = "c"
d = "d"
b = "b"
c = "c"
d = "d"
b = "b"
c = "c"
d = "d"
b = "b"
c = "c"
d = "d"
```
@[2](これは"b"です)
@[23](これは"c"です)


---

# h1

## h2

### h3

大文字になるっぽいな

---

# 箇条書きのテスト

- aaa
- bbb
- ccc |
- ddd
- eee
- fff |
- ggg

---

### おわり

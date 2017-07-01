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

### Crsytalってどんな感じなのか

---

## GOALS

- Have a syntax similar to Ruby (but compatibility with it is not a goal) |
- Statically type-checked but without having to specify the type of variables or method arguments. |
- Be able to call C code by writing bindings to it in Crystal. |
- Have compile-time evaluation and generation of code, to avoid boilerplate code. |
- Compile to efficient native code. |

---

### Syntax

```crystal
class MyStrPrinter
  def initialize(@greeting : String = "", @name : String = "")
  end

  def print
    puts "#{@greeting}, #{@name}."
  end
end

s = MyStrPrinter.new(name: "Taro", greeting: "Hello")
s.print  # => Hello, Taro.
```
@[2](インスタンス変数に直接代入される)
@[10](通常の変数名を使ったキーワード引数)

---

### Short one-argument syntax

A short syntax exists for specifying a block that receives a single argument and invokes a method on it.

```crystal
puts ["abc", "def", "ghi"].map do |arg|
  arg.upcase.reverse
end
# => ["CBA", "FED", "IHG"]

# ditto
puts ["abc", "def", "ghi"].map(&.upcase.reverse)
```
@[1-4]()
@[6-7]()

[Crystal Docs - Blocks and Procs](https://crystal-lang.org/docs/syntax_and_semantics/blocks_and_procs.html)

---

### Union types

```crystal
if 1 + 2 == 3
  a = 1
else
  a = "hello"
end

a      # : Int32 | String
a.to_s # => String
a + 1  # Error, because String#+(Int32) isn't defined
```
@[1-5]()
@[7]()
@[8]()
@[9]()

[Crystal Docs - Union types](https://crystal-lang.org/docs/syntax_and_semantics/union_types.html)

---

# 🙅

```
undefined method 'to_i' for Nil (compile-time type is (Array(Array(Bool | Float64 | Int32 | Int64 | MySQL::Types::Date | Slice(UInt8) | String | Time | Nil)) | Nil)) (did you mean 'to_s'?)
```

###### 　

- 変数のスコープは小さくする |
- 変数の型を明示的に書いてしまう |

---

### Macros

```crystal
class MacroSample
  macro define_getter(*names)
    {% for name in names %}
      def {{name}}
        @{{name}}
      end
    {% end %}
  end

  define_getter year, month, date, hour, min, sec
end

# ditto (at compile-time)
class MacroSample
  def year
    @year
  end

  def month
    @month
  end

  def date
    @date
  end

  def hour
    @hour
  end

  def min
    @min
  end

  def sec
    @sec
  end
end
```
@[1-11]()
@[2-8](Macroの定義)
@[10](Macroの呼び出し)
@[13-38](compile-time時のコード)
---

### Generics

```crystal
class MyBox(T)
  def initialize(@value : T)
  end

  def value
    @value
  end
end

int_box = MyBox(Int32).new(1)
int_box.value # => 1 (Int32)

string_box = MyBox(String).new("hello")
string_box.value # => "hello" (String)

another_box = MyBox(String).new(1) # Error, Int32 doesn't match String
```
@[1-8](大文字で型変数を定義)
@[10-11](Int32のオブジェクトを生成)
@[13-14](Stringのオブジェクトを生成)
@[16](型が違うとError)

---

### abstract class

```crystal
# abstract.cr
abstract class Animal
  abstract def talk
end

class Dog < Animal
end
#  Error in abstract.cr:2: abstract `def Animal#talk()` must be implemented by Dog
#
#    abstract def talk
#                 ^~~~
```

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

###### ライブラリをinstallするまでの流れ

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
Initialized empty Git repository in /path/to/kemal_test/.git/
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
$ ls -1 lib
kemal
kilt
radix

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
@[42-46](libディレクトリにあります)
@[47](ソースコードを編集します)
@[48]()
@[49-57](`require`できます)
@[58-59](実行できます)

---

### ライブラリを紹介しているサイト


---

### [AWESOME CRYSTAL](http://awesome-crystal.com/)

<img src="assets/images/awesome-crystal.png" width="60%">


---

### [CrystalShards](http://crystalshards.xyz/)

<img src="assets/images/crystalshards-xyz.png" width="60%">


---

### 有名だと思うもの

- [kemal](http://kemalcr.com/)
  - Sinatraライクな web framework
- [amber](http://www.ambercr.io/)
  - Railsライクな web framework
  - CLIツールもある
- [sidekiq.cr](http://www.mikeperham.com/2016/05/25/sidekiq-for-crystal/)
  - sidekiq作者が自ら制作

---

### 最近少し注目しているもの

- [graphql-crystal](https://github.com/ziprandom/graphql-crystal)
  - まだbeta版
- [scry](https://github.com/kofno/scry)
  - LSP対応の code analysis server

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

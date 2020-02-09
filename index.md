---
marp: true
theme: "black"
transition: "none"
header: "REEDEX"
footer: "技術交流会 2020/02"
---

# 2020/02 技術交流会

今月のニュースと雑感纏め

---



# Vue.js関連
## ベストプラクティスについて
[Vue開発者のためのVue.jsベストプラクティス集15選](https://qiita.com/mtoyopet/items/87a32d8e3497c5421727)


---

# Vue.js関連
## 事例紹介
[Vue.jsで作成された、ちょっと面白くて役立ちそうなサービス - Qiita](https://qiita.com/s-yoshiki/items/51150b37153b41df1da6)


---

# ツール紹介
## プロジェクトの情報を一か所に集約するツール
[Notion](https://www.notion.so/)


---

# Windows7は死なない その1

[GIZMODO JAPAN: サポート終了したはずのWindows 7にアプデ配信が決定！](https://www.gizmodo.jp/2020/01/microsoft-new-windows-7-update.html)

---

# Windows7は死なない その2

[もう不要ならWindows7をオープンソース化しろ！](https://forest.watch.impress.co.jp/docs/serial/yajiuma/1231926.html)



---

# JavaScript関連

[JavaScriptエンジンの仕組みをGIFアニメで分かりやすく解説 | コリス](https://coliss.com/articles/build-websites/operation/javascript/javascript-visualized-the-javascript-engine.html)

---

# JavaScript関連
TypeScriptの話

[この TypeScript が Hello, world! のくせに慎重すぎる - Qiita](https://qiita.com/matzkoh/items/90baab22ad489b78384b)

---

# ニュースサイト紹介

プログラマ用ニュースサイト[TechFeed](https://techfeed.io/main/realtime/000000000000000000000000)
の、Pro版が出たそうですよ

[CodeZine（コードジン）: ITエンジニア向け情報サービスのエキスパート特化版「TechFeed Pro」のクローズドβがリリース](https://codezine.jp/article/detail/11939)


---


# ブラウザ関連

---

# ブラウザ関連
## Flash
[GIZMODO JAPAN: Flash、とうとうSafariプレビュー版にインスコできなくなる](https://www.gizmodo.jp/2020/01/flash-safari.html)


---

# ブラウザ関連
## ユーザーエージェント

[ユーザーエージェント（UA）文字列は時代遅れ？ ～「Google Chrome」で凍結・非推奨に](https://forest.watch.impress.co.jp/docs/serial/yajiuma/1229968.html)


---

# 最近仕事でハマった話

クラスを初期化する際に、C#にて多用している書き方がこちら

* 引数沢山のコンストラクタ書かなくていい
* 初期化時の{}内でメンバの過不足が分かる

---

```C#
class A {
    public string id { get; private set; }
    public string name { get; private set; }
}

var a = new A() {
    // この中でコード補完が効く
    id = "id",
    name = "name",
};
```
---

今Javaやってるんだけれど、Javaで似たような書き方ないかなあ

---

あった

``` Java
class A {
    public String id;
    public String name;
}

var a = new A() {
    {
        id = "id"
        name = "name";
    }
};
```

---

Lombok使ってる場合

``` Java
import Lombok.Value;

@Value
class A {
    private final String id;
    private final String name;
}

var a = new A() {
    {
        setId("id");
        setName("name");
    }
};
```

---

ちょっと気持ち悪いけどまあいいや！

---

が、この初期化をO/RマッパーのEntityクラスに使用するとまともに動作しない不具合が発生

---

この書き方が原因だということは分かったので全て書き直した

---

その後、どうしてそうなるのかを探して検索していると以下の記事を発見

[JavaでもC#みたいなオブジェクト初期化子書けるんですよ](http://cs.hatenablog.jp/entry/2013/06/24/190945)

---

記事引用

「コンストラクタ呼び出し直後に{ }ブロックを置くと匿名クラスの宣言・初期化になります。」

---

記事引用

「C#ととても似た目で同じような記述ができるのですが内部的な意味はまったく異なるわけです。

一時変数を一個追い出すために匿名クラスが一本できるわけで、これは省資源的にいかがなものかと言われればその通りですが、ラムダ式が一行にできるかできないかってときは正当化されそうです。」

---

記事引用

「あと、厳密にPersonインスタンスを要求しているところに匿名拡張Personを渡したりすると当然怒られるので相手は選んでください。」

---

記事引用

「***厳密にPersonインスタンスを要求しているところに匿名拡張Personを渡したりすると当然怒られる***」

---

この不具合の発見が19時くらいで、解明したのが21時頃でした

---

みなさんも、

よくわからずに書いている文法が、実は思ってたことと違う！

なんてことはありませんか？


---

よくよく気を付けましょう

---

# 他何かありましたか？

また、次回以降こういう系統のニュースを集めてほしいというのがあれば頑張ります


例えば
* 言語/ライブラリのリリース情報
* 開催前イベント
* Qiita記事

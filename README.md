# くお〜!!Unused CSS selector〜!!ここでonwarn全開、インド人を=>に！

この記事は[SvelteKitのカレンダー | Advent Calendar 2022 - Qiita](https://qiita.com/advent-calendar/2022/sveltekit)の20日目となる投稿です。

movie

## 概要

SvelteKitは、使用されていないCSSを実行時に表示してくれる便利な機能が備わっています。

![使用されていないCSSの例]()

使用されていないCSS

![通知されたメッセージの例]()

実行時に通知されたメッセージ

今回の投稿では、この便利な機能の裏に潜む陰惨な社会の歪に迫ってみたいとおもいます。

## くお〜!!Unused CSS selector〜!!

結論からまず述べると、歪んでいたのは社会ではなく、自分自身の認知だったのです。なんということでしょう。

使用されていないCSSを教えてくれるとても便利なこの機能ですが、あえて使用しないCSSを残しておきたいこともあるでしょう。
１つや２つの通知であれば、生体ignoreで無視することもできなくはないかとおもいます。
しかし、Svelteのために作られたものではない、外部ライブラリなどではそうはいきません。

ここでは、TailwindCSSのプラグイン、DaisyUIを使って、@applyでクラスを呼び出した場合の例を示してみましょう。

Movie

**「くお〜!!Unused CSS selector〜!!」**


## インド人を=>に！ とは

残念ながら、現在ではこのUnused CSS selectorの通知をいい感じに制御する方法は用意されていないようです。容易ではないのかも。<br>※筆者が知らないだけの可能性も高いです。

ということで、インド人を=>にします。

**サンプルコード svelte.config.js**

```javascript

```

このサンプルコードは、rollup.config.js向けの内容のものをsvelte.config.jsに書いてみたのですが、よくわからないけど動いたので良かったです。<br>
onwarnでhandlerとwarningを受け取ってなんやかんやします。<br>
あと、もうなんか疲れていたのでwarningの持つcodeがcss-unused-selectorの通知を、全てreturnしているのでSvelteKitとの仲が疑われます。

SvelteKitとはこれからも仲良くしていきたいので、warningの中を確認して、frameとかの語句から、通知無視が自明なものをピンポイントで設定しても良いでしょう。

![warningを出力した様子]()

warningをご覧ください

![個別に指定されたonwarn]()

個別に指定してみました

![通知が制御された様子]()

やったぜ！！

## まとめ

社会の歪、それはお昼ご飯までちょっと時間があるし、エラー通知でも消しとくかとおもった事による運の尽きでした。もっと賢い解決方法はないのかと夜が更けるまで挑戦し続けた結果、賢い方法は賢くないと解決できないのでは？ という結論に至り、今回の投稿とさせて頂きました。

もっと賢い解決方法が世間に周知される未来を夢見て。 【完】

**※注：例示したDaisyUIに関しては、@applyで呼ばなければそもそも問題ないかも。**

### 参考文献

> [Unused css selector warning - disable specific parts? · Issue #1594 · sveltejs/svelte · GitHub](https://github.com/sveltejs/svelte/issues/1594)

## Next

明日のSvelteKit Advent Calendar 2022は...<br>
[SvelteKitのカレンダー | Advent Calendar 2022 - Qiita](https://qiita.com/advent-calendar/2022/sveltekit)
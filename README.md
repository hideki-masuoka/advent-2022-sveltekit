# くお〜!!Unused CSS selector〜!!ここで onwarn 全開、インド人を=>に！

この記事は[SvelteKit のカレンダー | Advent Calendar 2022 - Qiita](https://qiita.com/advent-calendar/2022/sveltekit)の 20 日目となる投稿です。

![これがUnused CSS selectorだ](https://raw.githubusercontent.com/hideki-masuoka/advent-2022-sveltekit/main/static/fig-00-eyecatch.png)

## 概要

SvelteKit は、使用されていない CSS を実行時に表示してくれる便利な機能が備わっています。

![使用されていないCSSの例](https://raw.githubusercontent.com/hideki-masuoka/advent-2022-sveltekit/main/static/fig-01-yay-im-unused.png)

使用されていない CSS

![通知されたメッセージの例](https://raw.githubusercontent.com/hideki-masuoka/advent-2022-sveltekit/main/static/fig-02-yay-im-unused-log.png)

実行時に通知されたメッセージ

今回の投稿では、この便利な機能の裏に潜む陰惨な社会の歪に迫ってみたいとおもいます。

## くお〜!!Unused CSS selector〜!!

結論からまず述べると、歪んでいたのは社会ではなく、自分自身の認知だったのです。なんということでしょう。

使用されていない CSS を教えてくれるとても便利なこの機能ですが、あえて使用しない CSS を残しておきたいこともあるでしょう。
１つや２つの通知であれば、生体 ignore で無視することもできなくはないかとおもいます。
しかし、Svelte のために作られたものではない、外部ライブラリなどではそうはいきません。

ここでは、TailwindCSS のプラグイン、DaisyUI を使って、@apply でクラスを呼び出した場合の例を示してみましょう。

![くお〜！](https://raw.githubusercontent.com/hideki-masuoka/advent-2022-sveltekit/main/static/unused-no-im-used.webp)

**「くお〜!!Unused CSS selector〜!!」**

## インド人を=>に！ とは

残念ながら、現在ではこの Unused CSS selector の通知をいい感じに制御する方法は用意されていないようです。容易ではないのかも。<br>※筆者が知らないだけの可能性も高いです。

ということで、インド人を=>にします。

**サンプルコード svelte.config.js**

```javascript
import adapter from '@sveltejs/adapter-auto';
import { vitePreprocess } from '@sveltejs/kit/vite';

/** @type {import('@sveltejs/kit').Config} */
const config = {
	// Consult https://kit.svelte.dev/docs/integrations#preprocessors
	// for more information about preprocessors
	preprocess: vitePreprocess(),

	kit: {
		adapter: adapter()
	},
	// ここでonwarn全開
	onwarn: (warning, handler) => {
		const { code } = warning;

		if (code === 'css-unused-selector') {
			return;
		}

		handler(warning);
	}
};

export default config;
```

このサンプルコードは、rollup.config.js 向けの内容のものを svelte.config.js に書いてみたのですが、よくわからないけど動いたので良かったです。<br>
onwarn で handler と warning を受け取ってなんやかんやします。<br>
あと、もうなんか疲れていたので warning の持つ code が css-unused-selector の通知を、全て return しているので SvelteKit との仲が疑われます。

SvelteKit とはこれからも仲良くしていきたいので、warning の中を確認して、frame とかの語句から、通知無視が自明なものをピンポイントで設定しても良いでしょう。

![warningを出力した様子](https://raw.githubusercontent.com/hideki-masuoka/advent-2022-sveltekit/main/static/fig-03-put-warning.png)

▲ warning をご覧ください

![個別に指定されたonwarn](https://raw.githubusercontent.com/hideki-masuoka/advent-2022-sveltekit/main/static/fig-04-frame-includes.png)

▲ 個別に指定してみました

![通知が制御された様子](https://raw.githubusercontent.com/hideki-masuoka/advent-2022-sveltekit/main/static/fig-05-compile-done.png)

▲ やったぜ！！

## まとめ

社会の歪、それはお昼ご飯までちょっと時間があるし、エラー通知でも消しとくかとおもった事による運の尽きでした。もっと賢い解決方法はないのかと夜が更けるまで挑戦し続けた結果、賢い方法は賢くないと解決できないのでは？ という結論に至り、今回の投稿とさせて頂きました。

もっと賢い解決方法が世間に周知される未来を夢見て。 【完】

**※注：例示した DaisyUI に関しては、@apply で呼ばなければそもそも問題ないかも。**

### 参考文献

> [Unused css selector warning - disable specific parts? · Issue #1594 · sveltejs/svelte · GitHub](https://github.com/sveltejs/svelte/issues/1594)

## Next

明日の SvelteKit Advent Calendar 2022 は...<br>
[SvelteKit のカレンダー | Advent Calendar 2022 - Qiita](https://qiita.com/advent-calendar/2022/sveltekit)

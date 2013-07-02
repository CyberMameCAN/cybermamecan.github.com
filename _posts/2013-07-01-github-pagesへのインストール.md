---
layout: post
title: Jekyll + GitHub Pages
date: 2013-07-01
excerpt: Jekyllを使っていて少し不満があったので、GitHub Pagesをマイドメインで使う事にしたので、その忘備録です。
categories: Jekyll
tags: [エンジニアとして, git]
sumnail: jekyll-logo.png
---
このブログは[Jekyll](http://jekyllrb.com/)で作っています。  
Markdownでコーディングし、それをテンプレート（Liquid構文）に則って自動でHTMLへ変換してくれます。  
変換して作成されたHTMLやCSSファイル、画像などをWebサーバにアップすれば、面倒な設定も無く公開出来ます。  
簡単にHTMLを生成出来る優れものです。

##<span>ちょっとした不満</span>
ただ一つ、Jekyllに不満があるとしたら、一つファイルを修正する事で全ファイルが再作成される事です。  
FTPソフトはPanic社のTransmitを使ってWebサーバと同期をするようにしてますが、ファイルの作成日が変わってしまうため結局すべてのファイルをアップロードし直しとなってしまいます。

これを解決するにはやっぱり[GitHub Pages](http://pages.github.com)を利用するのが一番かな、という結論に至りました。  
GitHub PagesはJekyllで構築されたファイルをGitHubへアップロードすればあっという間に公開できてしまう大変面白いものです。
もちろん無料なんです。

ちょっと前フリが長かったですが、GitHub Pagesを作ってマイドメインで表示されるところまで忘備録も兼ねて残してみます。

##<span>リポジトリ作成</span>

[GitHub](https://github.com)にアクセスしたら右上の<b>アイコン（create a new repo）</b>をクリックします。  
<p class="img_position"><img src="/assets/images/1.Create-a-new-repo.png" alt="Create a new repo" width="" /></p>
Repository nameは<b>username.GitHub.com </b>を入力します。  
「username」は作った自分のIDですが、この同じIDで作らないとGitHub PagesにWebサイトとして反映されないようです。

##<span>GitHubへpush</span>
Jekyllのルートに移動して次のコマンドを実行して行けばGitHub Pagesに数分で反映されるようになります。
{% highlight sh linenos %}
$ git add .
$ git commit -m "first commit"
$ git remote add origin https://GitHub.com/username/username.github.com.git
$ git push -u origin master
{% endhighlight %}

##<span>マイドメインで運用する時</span>
これは<b>サブドメイン</b>の場合です。

###<span>ドメインの設定</span>
種別を*別名(CNAME)*、値を*username.github.io.*にそれぞれ指定し、githubのサイトを見に行くように設定します。  
（username.github.io.の一番最後にピリオドをお忘れなく。）

###<span>Jekyllの設定</span>
JekyllのルートにCNAMEというファイルを作って運用したいURLを記述し、GitHubへpushします。

以上でドメインが浸透すればマイドメインで表示されるようになるはずです。



---
layout: post
title: "How to Install Octopress Blog with Github?"
date: 2014-06-25 16:17:17 +0800
comments: true
categories: [Git, Github, Octopress, Blog, Markdown]
Author: shaching
---

之前陸陸續續用過倒掉的無名、Pixnet 和 Blogger，

這些 Blog 的編輯排版非常麻煩，尤其是要貼 Code 的時候...WTF

所以後來有一大段時間沒在寫，但隨著年紀增長開始健忘XD

因此決定找一個好用的 Blog 來防呆...

找了許久終於找到好吃的 Octopress，

Markdown 語法解決了我最討厭的排版問題，

還可以用 Vim + Git 來編輯和發布文章，

整個就是超級符合我這個懶人的 Style。

不過網路上的安裝教學文章大多是 2012 年左右的，

而我在安裝過程中也遇到些問題折騰了不少時間，

為了不再重蹈覆轍，所以通通記錄下來。

<!--more -->

**Step0. 環境需求**

我用的作業系統是 Lubuntu 14.04 64bit，Windows 的我就幫不上忙啦。

**Step1. 建立自己的Github帳號**

沒有帳號的人要先到 [https://github.com/](https://github.com/) 註冊，

接下來要 new 一個 repository 用來存放你的 Blog 資料，

Repository name 要填入 username.github.io

而 username 就是你剛剛申請的 Github 帳號名稱，

接著直接點網頁最下面的 Create Repository 按鈕。

**Step2. 安裝Octopress**

官方說明網頁：[Octopress Setup](http://octopress.org/docs/setup/)

安裝 Git
```
$ sudo add-apt-repository ppa:git-core/ppa
$ sudo apt-get update
$ sudo apt-get install git
$ git config --global user.name "yourname"            # Enter your name
$ git config --global user.email "yourname@email.com" # Enter your Email
```

安裝 Node.js (問題1)
```
$ sudo apt-get install nodejs
```

安裝 Curl
```
$ sudo apt-get install curl
```

安裝 rvm
```
$ curl -L https://get.rvm.io | bash -s stable --ruby
```

安裝 Ruby 1.9.3
```
$ rvm install 1.9.3
$ rvm use 1.9.3
$ rvm rubygems latest
$ ruby --version      # It should be Ruby 1.9.3
```

安裝 Octopress
```
$ git clone git://github.com/imathis/octopress.git octopress
$ cd octopress
$ gem install bundler
$ bundle install
$ rake install
```

**Step3. 設定Octopress**

官方說明網頁：[Deploying](http://octopress.org/docs/deploying/)

執行下列指令來設定 Github 的位置
```
$ rake setup_github_pages
```

接著輸入 git@github.com:username/username.github.io.git

username 一樣是剛剛申請的 Github 帳號名稱。

然後用 vim 編輯 \_config.yml 設定網頁資訊，

下列是我修改的部份，其它的細節可以到官網看 [Configuring Octopress](http://octopress.org/docs/configuring/)。
```
title: 月光寶盒
subtitle: Less is More
author: shaching
...
google_plus_one: true
google_plus_one_size: medium
facebook_like: ture
```

接著執行產生網頁和發布網頁
```
$ rake generate
$ rake deploy
$ git add .
$ git commit -m 'init'
$ git push origin source
```

接著打開瀏覽器輸入網址 http://username.github.io

等約10分鐘就可以看到 Octopress 的網頁 (問題2)。

**Step4. 發布新文章**

官方說明網頁：[Blogging Basics](http://octopress.org/docs/blogging/)

執行以下指令產生新文章
```
$ rake new_post["How to Install Octopress Blog with Github?"]
```

Octopress 會產生文章檔案在 source/\_posts/ 底下，用 vim 編輯完成後存檔。
```
$ vim source/_posts/2014-06-25-how-to-install-octopress-blog-with-github.markdown
```

(因為 Octopress 使用 Markdown 語法，可以到 [Markdown文件](http://markdown.tw/) 學習。)

(不惜慣用 vim 編輯的人，推薦 real-time preview 的 ReText 編輯器，安裝方式如下。)
```
$ sudo apt-get install retext
```

編輯完成後要先執行以下指令
```
$ rake generate  # Generates posts and pages into the public directory
$ rake watch     # Watches source/ and sass/ for changes and regenerates
$ rake preview   # Watches, and mounts a webserver at http://localhost:4000 
```

打開瀏覽器輸入 http://localhost:4000 便可預覽文章，

確定沒問題後要再做一次發布網頁動作。
```
$ git add .
$ git commit -m 'How to Install Octopress Blog with Github?'
$ git push origin source
$ rake deploy
```

最後就是你現在看到的這篇文章啦～^^

**問題1.**

執行 $rake generate 時候會遇到 Could not find a JavaScript runtime，請安裝 nodejs 套件。
```
$ rake generate

## Generating Site with Jekyll
identical source/stylesheets/screen.css 
/home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/execjs-2.2.0/lib/execjs/runtimes.rb:51:in `autodetect': Could not find a JavaScript runtime. See https://github.com/sstephenson/execjs for a list of available runtimes. (ExecJS::RuntimeUnavailable)
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/execjs-2.2.0/lib/execjs.rb:5:in `<module:ExecJS>'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/execjs-2.2.0/lib/execjs.rb:4:in `<top (required)>'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/coffee-script-2.2.0/lib/coffee_script.rb:1:in `require'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/coffee-script-2.2.0/lib/coffee_script.rb:1:in `<top (required)>'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/coffee-script-2.2.0/lib/coffee-script.rb:1:in `require'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/coffee-script-2.2.0/lib/coffee-script.rb:1:in `<top (required)>'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/jekyll-coffeescript-1.0.0/lib/jekyll-coffeescript.rb:2:in `require'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/jekyll-coffeescript-1.0.0/lib/jekyll-coffeescript.rb:2:in `<top (required)>'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/jekyll-2.0.3/lib/jekyll.rb:73:in `require'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/jekyll-2.0.3/lib/jekyll.rb:73:in `<top (required)>'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/jekyll-2.0.3/bin/jekyll:6:in `require'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/gems/jekyll-2.0.3/bin/jekyll:6:in `<top (required)>'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/bin/jekyll:23:in `load'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/bin/jekyll:23:in `<main>'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/bin/ruby_executable_hooks:15:in `eval'
	from /home/johnny/.rvm/gems/ruby-1.9.3-p547/bin/ruby_executable_hooks:15:in `<main>'
```

**問題2.**

網頁發布後大約需要十分鐘後才能在 http://username.github.io 看到網頁，

我原本以為立刻可以看到文章...結果一直看到 404 page not found...囧，

害我一直以為有哪一個步驟錯了@@...嗯...多等個十分鐘吧！

---
title: "貼文語法"
date: 2021-07-17
last_modified_at: 2021-07-17
categories:
  - blog
tags:
  - post
---

## 增加貼文方法
只要在`_posts`中增加格式為`YYYY-MM-DD-name-of-post.md`並在其中加入適當的`front matter`(正文版面)即可


## 貼文摘要功能
此段文字會成為貼文的摘要，原因是我們有加入`<!--more-->`在此段文章前

可指定不同的`separator`，一般會設為`<!--more-->`

需要加在貼文`front matter`中，如下
```yaml
title: "ABC"
date: ...
last_modified_at: ...
excerpt_separator: "<!--more-->"
categories:
  - ABC
tags:
  - ABC
```

<!--more-->

## 貼文notice功能
利用notice功能能夠補充文章的細節或是在視覺上進行強調

將`{: .notice}`加在句尾能讓`.notice`被加入到`<p></p>`的html元素中，範例如下：

`{: .notice}`

**Notice:** 簡單的notice
{: .notice}

`{: .notice--primary}`

**Primary Notice:** 加深的notice，一般用在較為重要的notice
{: .notice--primary}

`{: .notice--info}`

**Info Notice:** 補充資訊的notice
{: .notice--info}

`{: .notice--warning}`

**Warning Notice:** 警告用的notice
{: .notice--warning}

`{: .notice--danger}`

**Danger Notice:** 顯示危險的notice
{: .notice--danger}

`{: .notice--success}`

**Success Notice:** 顯示成功的notice
{: .notice--success}

同時也能將多個段落或其他元素加入到notice，第一種作法是利用`capture`來決定notice的開始與結束，作法如下：

```html
{% raw %}{% capture notice-2 %}
#### ABC
* A
* B
* C
{% endcapture %}{% endraw %}
<div class="notice">{% raw %}{{ notice-2 | markdownify }}{% endraw %}</div>
```

{% capture notice-2 %}
#### ABC

* A
* B
* C
{% endcapture %}

<div class="notice">
  {{ notice-2 | markdownify }}
</div>

第二種方法是直接使用HTML語法：
```html
<div class="notice">
  <h4>ABC</h4>
  <p>A.</p>
</div>
```

<div class="notice">
  <h4>ABC</h4>
  <p>A.</p>
</div>

## 貼文引用功能
利用`>`來顯示引用的話：

> ABC

> <cite><a href="https://www.google.com.tw/">Google 台灣首頁</a></cite>

## 貼文連結功能
可以將`link: http://url-you-want-linked`加在貼文`front matter`中，使點擊貼文時能直接連結到指定的頁面：

```yaml
title: "Post: Link"
categories:
  - Blog
tags:
  - link
  - Post Formats
link: https://github.com
```

## 貼文超連結功能
一般超連結可以以`[文字](超連結URL)`的方式加入到文章中，不過若要重複使用該超連結，則應該以定義變數的方式如下：

```markdown
文章文章文章[Google][google-site]文章文章文章

[google-site]: https://www.google.com.tw/
```

文章文章文章[Google][google-site]文章文章文章

[google-site]: https://www.google.com.tw/

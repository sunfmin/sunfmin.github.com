---
layout: post
title: Jekyll no access permission to `/'
---

When I start jekyll with:

	jekyll --server

And I access the page, it gives me:

	FelixMBPR:sunfmin.github.com sunfmin$ jekyll --server
	Configuration from /Users/sunfmin/Developments/sunfmin.github.com/_config.yml
	Auto-regenerating enabled: /Users/sunfmin/Developments/sunfmin.github.com -> /Users/sunfmin/Developments/sunfmin.github.com/_site
	[2013-03-13 13:49:46] regeneration: 26 files changed
	[2013-03-13 13:49:47] INFO  WEBrick 1.3.1
	[2013-03-13 13:49:47] INFO  ruby 1.9.3 (2012-12-25) [x86_64-darwin12.2.1]
	[2013-03-13 13:49:47] INFO  WEBrick::HTTPServer#start: pid=49222 port=4000
	[2013-03-13 13:49:48] ERROR no access permission to `/'
	localhost - - [13/Mar/2013:13:49:48 CST] "GET / HTTP/1.1" 403 283

After searching google, and more frustration, I found: http://sebdah.github.com/blog/2012/10/02/debugging-jekyll/, Which explains I should do this, It gives error explainations, Which is best. secretly hidding error information is the worst thing you can do.

	FelixMBPR:sunfmin.github.com sunfmin$ jekyll --no-auto --server
	Configuration from /Users/sunfmin/Developments/sunfmin.github.com/_config.yml
	Building site: /Users/sunfmin/Developments/sunfmin.github.com -> /Users/sunfmin/Developments/sunfmin.github.com/_site

	ERROR: YOUR SITE COULD NOT BE BUILT:
	------------------------------------
	(<unknown>): found unexpected ':' while scanning a plain scalar at line 3 column 9 in /Users/sunfmin/Developments/sunfmin.github.com/_posts/2011-12-14-cannot-decode-object-of-class.md


In my case, It is that you can not put `:` and `[]` in your blog title.

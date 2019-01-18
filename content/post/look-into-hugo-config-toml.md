---
title: "Look into hugo config.toml"
date: 2019-01-18T15:38:38+09:00
draft: true
---

# Hugo 테마

Hugo 블로그를 생성하고 테마를 적용하게 되면 제일 먼저 접하게 되는 것이 config.toml 파일이다.
toml은 Hugo를 사용하면서 처음보는 확장자였다. [(TOML)](https://github.com/toml-lang/toml) 

내가 사용중인 테마를 커스터마이징 하면서 config.toml 파일의 속성들이 어떻게 사용되는지 정리해 본다.

현재 사용하고 있는 테마는 [Icarus](https://github.com/digitalcraftsman/hugo-icarus-theme) 테마이다.

첫 블럭은 홈페이지의 기본설정으로 보면 된다. 항목 별로 주석을 달아 두었다.

~~~toml
# github 블로그 주소
baseurl = "https://wooilkim.github.io/"

# 사용 언어
languageCode = "en-us"

# github 블로그 주소
title = "Wooil"

# Disqus는 댓글 서비스를 제공하는 서비스다. 
# 블로그에 댓글 기능을 달려면 Disqus에 가입해 Shortname을 여기에 적으면 된다.
disqusShortname = "WooilKim"

# Google Analytics는 홈페이지 관련해 방문자에 대한 정보를 수집해 통계정보를 분석할 수 있는 서비스다. 
# 역시 가입해서 코드를 적으면 된다.
googleAnalytics = "UA-132678781-1"

# 한 페이지의 포스트 개수를 정한다.
paginate = 10

# TODO : 추후 설명 추가
footnotereturnlinkcontents = "↩"

# 테마 폴더와 테마이름을 입력한다. 
# themesDir과 theme를 이어서(./themes/icarus) 현재 사용하는 테마폴더를 가리켜야한다. 
# "./"는 현재 폴더를 가리킨다.
themesDir = "./themes/"
theme = "icarus"
~~~

- [Disqus](https://disqus.com)
- [Google Analytics](https://analytics.google.com)

이후 부분들은 [xxx]으로 묶여있는 형태이다. 들여쓰기 된 속성들이 하위속성으로 호출될 수 있다.

## permalinks

~~~toml
[permalinks]
    post = "/:year/:month/:day/:slug"
~~~

> 포스트의 URL 주소를 결정하는 속성이다.
> 아래 형식대로라면 작성일을 기준으로 "홈페이지주소/년/월/일/제목"의 url을 갖게된다.
새로운 포스트를 만들면 [Hugo 새로운 Post 작성하기]() 아래와 같은 내용을 가진 파일이 생성된다.

~~~md
---
title: "Look into hugo config.toml"
date: 2019-01-18T15:38:38+09:00
draft: true
---
~~~


[Hugo url-management](https://gohugo.io/content-management/urls/) 참조


~~~toml
[params]
    # Tell me who you are
    author = "Wooil Kim"
    bio = "Blogger - Programmer - Researcher"
    location = "Seoul, Republic of Korea"
    site_description = ""
    copyright  = "Powered by [Hugo](//gohugo.io). Theme by [PPOffice](http://github.com/ppoffice)."
    avatar = "css/images/avatar.png"
    # Enter your email address to display your Gravatar icon in the profile. If not set the theme
    # will fallback to the avatar.
    gravatar = "wooilkim@korea.ac.kr"
    logo = "css/images/logo.png"
    disable_mathjax = false # set to true to disable MathJax

    # define which types of pages should be shown. By default the type with the most regular pages
    mainSections = ["post"]

    # Format dates with Go's time formatting
    date_format = "2006-01-02"

    # Add custom assets with their paths relative to the static folder
	custom_css = []
	custom_js  = []
~~~

~~~toml
# Create custom menu entries by defining a label and a link for
# them. Since you can also link posts, you've the option the
# place the links before or after them.
#
# E.g.: "Home" appears before all linked posts in the menu
# and "Tags" / "Categories" after them.
[[params.menu]]
    before = true
    label  = "Home"
    link   = "/"

[[params.menu]]
    before = false
    label  = "Tags"
    link   = "tags/"

[[params.menu]]
    before = false
    label  = "Categories"
    link   = "categories/"

[[params.menu]]
    before = false
    label  = "About"
    link   = "about/"

# Enter a link for the follow button on the left
[params.profile]
    follow_button = "https://github.com/wooilkim"


[social]
# Add your social network accounts to the profile section on the left
# by entering your username. The links to your account will be
# created automatically.
    github          = "wooilkim"
    gitlab          = ""
    bitbucket       = ""
    jsfiddle        = ""
    codepen         = ""
    foursquare      = ""
    dribbble        = ""
    deviantart      = ""
    behance         = ""
    flickr          = ""
    instagram       = ""
    youtube         = ""
    vimeo           = ""
    vine            = ""
    medium          = ""
    wordpress       = ""
    tumblr          = ""
    xing            = ""
    linkedin        = "wooilkim"
    slideshare      = ""
    stackoverflow   = ""
    reddit          = ""
    pinterest       = ""
    googleplus      = ""
    facebook        = ""
    facebook_admin  = ""
    twitter_domain  = ""
    twitter         = ""

# Enable and disable widgets for the right sidebar
[params.widgets]
    recent_articles = true
    categories = true
    tags = true
    tag_cloud = true
~~~


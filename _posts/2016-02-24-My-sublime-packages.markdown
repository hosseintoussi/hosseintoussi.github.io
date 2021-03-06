---
layout: post
title:  "My Sublime Text Editor Packages and Customisations"
date:   2016-02-24 1:57:41
categories: dev-env
---
## **Packages**

### GitGutter
A plugin to show an icon in the gutter area indicating whether a line has been inserted, modified or deleted.
[Github repo](https://github.com/jisaacks/GitGutter)

### GitSavvy
A sublime text 3 plugin to provide basic git functionalities like: `init`, `add`, `commit`, `checkout`, `pull`, `push`.
[Github repo](https://github.com/divmain/GitSavvy)

### Emmet
It adds HTML, CSS shortcuts. With it's abbreviations you can quickly generate blocks.
[Github repo](https://github.com/sergeche/emmet-sublime)

Example:

{% highlight html %}
#page>div.logo+ul#navigation>li*5>a{Item $}
{% endhighlight %}

with a `tab` it becomes:

{% highlight html %}
<div id="page">
    <div class="logo"></div>
    <ul id="navigation">
        <li><a href="">Item 1</a></li>
        <li><a href="">Item 2</a></li>
        <li><a href="">Item 3</a></li>
        <li><a href="">Item 4</a></li>
        <li><a href="">Item 5</a></li>
    </ul>
</div>
</code>
</pre>
{% endhighlight %}

### Origami
A nice way of dealing with panes as you need them.
[Github repo](https://github.com/SublimeText/Origami)

### SideBarEnhancements
Enhances the operations on Sidebar of Files and Folders.
[Github repo](https://github.com/titoBouzout/SideBarEnhancements)

### Material Theme
The most epic theme for Sublime Text 3!
[Github repo](https://github.com/equinusocio/material-theme)

### BeautifyRuby
Reformats/Reindentes your ruby codes.
[Github repo](https://github.com/CraigWilliams/BeautifyRuby)

### Sublime Rubocop
It runs [Rubocop](https://github.com/bbatsov/rubocop) on your Ruby files in the Editor.
[Github repo](https://github.com/pderichs/sublime_rubocop)

## **Other customisations**

### Key Bindings
I have two key bindings:

- Toggle SideBar using `Command+\`.
- Toggle Minimap using `Command+shift+\`.

{% highlight json %}
[
	{ "keys": ["super+\\"], "command": "toggle_side_bar" },
	{ "keys": ["super+shift+\\"], "command": "toggle_minimap" }
]
{% endhighlight %}

### User Settings
Two settings worth mentioning:

- Trim trailing white spaces on save.
- Changing tab size to two spaces.

{% highlight json %}
[
	"trim_trailing_white_space_on_save": true,
	"tab_size": 2
]
{% endhighlight %}





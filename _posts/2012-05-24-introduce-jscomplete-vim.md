---
layout: post
title: Introduce jscomplete-vim
description: jscomplete-vim is the modern complement Vim plugin for JavaScript guys.
---

[jscomplete-vim][jscomplete-vim] is the modern complement Vim plugin for JavaScript guys.

### Using as omnifunc

Set `jscomplete#CompleteJS` to `omnifunc` in your `.vimrc` like this.

	autocmd FileType javascript setlocal omnifunc=jscomplete#CompleteJS

Then available auto complement properties after `.`, `[` keywords.

### Using as neocomplcache plugin

[neocomplcache][neocomplcache] is the Vim plugin to keyword completion. No more is necessary to basically using.

### Optional extensions

Extension scripts under the `autoload/js/` will be loaded with set list to `g:jscomplete_use` or `b:jscomplete_use` in your `.vimrc` like this.

	let g:jscomplete_use = ['dom', 'moz']

- `dom`: Adding DOM keywords completion.
- `moz`: Adding Mozilla JavaScript keywords completion.
- `dom`: Adding Mozilla XPCOM component keywords completion.

[jscomplete-vim]: https://github.com/teramako/jscomplete-vim
[neocomplcache]: https://github.com/Shougo/neocomplcache

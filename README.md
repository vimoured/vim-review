# vim-review

The file format for review comments, used by
[fugitive-extras](https://github.com/vimoured/fugitive-extras) and
[vim-prompts](https://github.com/vimoured/vim-prompts). Plugins call it; it has
nothing to type.

**Vim or Neovim:** tested on Vim 9.1 and newer. It's plain Vimscript, so it may
work on Neovim, but that's untested.

## Install

```vim
Plug 'vimoured/vim-review'
```

## Format

```
src/app.py:12: could you check the None case here?
src/app.py:20-24: is this loop needed?
	It seems to repeat line 8.
```

One comment per line, `path:line: text` or `path:start-end: text`, with further
lines tab-indented.

## Functions

A comment is `{path, start, end, body}`.

| Function | What it does |
| --- | --- |
| `review#read(file)` | The comments in `file` as `{comments, skipped}`; `skipped` counts lines not in the format. |
| `review#write(file, comments)` | Write `comments` to `file`, replacing it. |

## Tests

The specs in [vim-suite](https://github.com/vimoured/vim-suite) define what it
does: `test/vim-review.vim`.

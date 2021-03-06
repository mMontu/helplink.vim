[![This project is considered finished](https://img.shields.io/badge/Status-finished-green.svg)](https://arp242.net/status/finished)

Introduction
============
Link to Vim help pages with ease.

There are several sites which host the Vim help pages in formatted HTML. It's
often quite useful to link to this when explaining something.

With this plugin you can make a link to the help section you're viewing. Just
use `:Helplink`.

I originally wrote this here:
http://meta.vi.stackexchange.com/a/1250/51

Commands
========
:Helplink {format}                                                 `:Helplink`

Try to find the tag closest to the cursor (backwards search only) and
format it. If multiple tags are found on the same line, it asks the
user which one to pick.

This will echo the formatted URL and copy them to the registers in
`g:helplink_copy_to_registers`.

You can {format} parameter to get a different format; if not given the
value of `g:helplink_default_format` is used.

Options
=======
`g:helplink_copy_to_registers`                      (List, default: ['+', '\*'])

Automatically copy the link to these registers.

`g:helplink_url`                                 (URL, default:
http://vimhelp.appspot.com/%%FILE%%.html#%%TAGNAME_QUOTED%%)

Available placeholders:
- `%%FILE%%`            File name (e.g. `options.txt`)
- `%%TAGNAME%%`         Tag name (e.g. 'expandtab')
- `%%TAGNAME_QUOTED%%`  The quoted tag name for use in URLS (e.g. %27expandtab%27)

`g:helplink_formats`                                        (dict, default:

    {
    \	'markdown':  "'[`:help ' . l:tagname . '`](' . l:url . ')'",
    \	'html': "'<a href=\"' . l:url . '\">:help ' . l:tagname . '</a>'",
    \	'bbcode': "'[url=' . l:url . '][code]:help ' . l:tagname . '[/code][/url]'"
    \}

This string is `eval`-ed, variables you can use are {l:tagname} and
{l:url}.

`g:helplink_default_format`                         (String, default: markdown)

Available formats:
- markdown
- html
- bbcode

You can add your own in `g:helplink_formats`.

Functions
=========
`helplink#link([{format}])`                                    `helplink#link()`

Implements the `:Helplink` command; the {format} is optional.

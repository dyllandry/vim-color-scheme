# Vim Color Scheme

I want to make my own color scheme.

I've got a document here that describes how I want it to be: https://docs.google.com/document/d/115NVbpEAICIbpLF4bPHMdcMsaUz0HUQX0bIIAgZARmI/edit?usp=sharing

# Development

## Progress

I found $VIMRUNTIME/syntax/shared/typescriptcommon.vim has at the bottom :hi commands where special typescript highlight groups are linked to existing ones.

```
...
hi def link typescriptAsyncFuncKeyword     Keyword
hi def link typescriptObjectAsyncKeyword   Keyword
hi def link typescriptAsyncFor             Keyword
hi def link typescriptFuncKeyword          Keyword
hi def link typescriptAsyncFunc            Keyword
hi def link typescriptArrowFunc            Type
hi def link typescriptFuncName             Function
hi def link typescriptFuncArg              PreProc
hi def link typescriptArrowFuncArg         PreProc
hi def link typescriptFuncComma            Operator
...
```
For example, those groups, like `typescriptAsnycFuncKeyword` are linked to the Keyword highlight group.

Instead of having all those different parts of the function have different highlight groups, I'd want them to all be the same. So the whole function declaration stands out in blue, or something.

I should make my own color scheme file, (in this repo and symbolically link it to the right vim location), where first reset the theme, then start making changes. Like making the background grey and the normal group dark grey.

## Easily see hex code colors

Use the vim plugin _colorizer_ to be able to see the color of hex-codes on your screen.

```
use {
  "norcalli/nvim-colorizer.lua",
  cmd = "ColorizerToggle",
  config = function()
    require("colorizer").setup()
  end,
}
```

Then use `:ColorizerToggle`

- #000
- #888
- #fff

## Code for existing vim color schemes

To see the code for all the built-in color schemes, type `:e $VIMRUNTIME/colors`.

## Vim readme for making color schemes

Can be found in vim repo: https://github.com/vim/vim/blob/master/runtime/colors/README.txt

## Highlight Groups

The color scheme is mainly defined using highlight groups. There are 2 types of highlight groups.

- The built-in highlight-groups (:h highlight-groups).
- The ones used for specific languages. For these, the name starts with the name of the language.

We can run the command :so $VIMRUNTIME/syntax/hitest.vim to see all the current active highlight groups.

We can use the :Telescope highlights command to see and search for the highlight groups.

## Treesitter Highlight Groups

If we navigate to $VIMRUNTIME/syntax, we can see the syntax definitions and the highlight group definitions for all the supported languages.

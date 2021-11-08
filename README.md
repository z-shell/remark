# `REMARKJS/REMARK` ZINIT PACKAGE

## Homepage link: [remarkjs/remark](https://github.com/remarkjs/remark)

| **Package source:** | Tarball | Git |       Node       | Gem |
|:-------------------:|:-------:|:---:|:----------------:|:---:|
|     **Status:**     |    -    |  -  | + <br> (default) |  –  |

[Zinit](https://github.com/z-shell/zinit) can use the NPM package registry
to automatically:

- get the plugin's Git repository OR release-package URL,
- get the list of the recommended ices for the plugin,
  - there can be multiple lists of ices,
  - the ice lists are stored in *profiles*; there's at least one profile, *default*,
  - the ices can be selectively overriden.

Example invocations that'll install
[remarkjs/remark](https://github.com/remarkjs/remark) by using the
[bin-gem-node](https://github.com/z-shell/z-a-bin-gem-node) annex:

```zsh
# Download the Node package of remark-cli, remark-man and remark-html
zinit pack for remark

# Download the Node package of remark-cli and remark-man
zinit pack"man-only" for remark

# Download the Node package of remark-cli and remark-html
zinit pack"html-only" for remark
```

## Default Profile

Provides the CLI command `remark` with two plugins: Man and Html.

The Node packages are installed locally into a null-plugin directory (feature of
the bin-gem-node annex) and provided to the command line through *shims*, i.e.:
automatic forwarder scripts created under `$ZPFX/bin` (which is added to the
`$PATH` by default; shims are also a bin-gem-node annex feature).

The Zinit command executed will be equivalent to:

```zsh
zinit lucid as=null \
    node="remark <- !remark-cli; remark-man; remark-html" \,
    sbin="n:node_modules/.bin/remark" for \
        z-shell/null
```

## `man-only` Profile

Provides the CLI command `remark` with single plugin: Man.

The Zinit command executed will be equivalent to:

```zsh
zinit lucid as=null \
    node="remark <- !remark-cli; remark-man" \,
    sbin="n:node_modules/.bin/remark" for \
        z-shell/null
```

## `html-only` Profile

Provides the CLI command `remark` with single plugin: Html.

The Zinit command executed will be equivalent to:

```zsh
zinit lucid as=null \
    node="remark <- !remark-cli; remark-html" \,
    sbin="n:node_modules/.bin/remark" for \
        z-shell/null
```

<!-- vim:set ft=markdown tw=80 fo+=an1 autoindent: -->

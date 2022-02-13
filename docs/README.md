<h2 align="center">
  <a href="https://github.com/z-shell/zi">
    <img src="https://github.com/z-shell/zi/raw/main/docs/images/logo.svg" alt="Logo" width="80" height="80" />
  </a>
❮ ZI ❯ Package - Remark
</h2>

<h3 align="center">

| **Package source:** | Tarball | Git |             Node             | Gem |
| :-----------------: | :-----: | :-: | :--------------------------: | :-: |
|     **Status:**     |    -    |  -  | :heavy_check_mark: (default) | :x: |

</h3>

- [Available `pack''` invocations](#available-pack-invocations)
- [Default Profile](#default-profile)
- [`man-only` Profile](#man-only-profile)
- [`html-only` Profile](#html-only-profile)

> This repository compatible with [ZI](https://github.com/z-shell/zi)

The [remarkjs/remark](https://github.com/remarkjs/remark) zsh package that can use the NPM package registry to automatically:

- get the plugin's Git repository OR release-package URL,
- get the list of the recommended ices for the plugin,
  - there can be multiple lists of ices,
  - the ice lists are stored in _profiles_; there's at least one profile, _default_,
  - the ices can be selectively overridden.

### Available `pack''` invocations

```zsh
# Download the Node package of remark-cli, remark-man and remark-html
zi pack for remark

# Download the Node package of remark-cli and remark-man
zi pack"man-only" for remark

# Download the Node package of remark-cli and remark-html
zi pack"html-only" for remark
```

### Default Profile

Provides the CLI command `remark` with two plugins: Man and Html.

The Node packages are installed locally into a null-plugin directory (feature of
the bin-gem-node annex) and provided to the command line through _shims_, i.e.:
automatic forwarder scripts created under `$ZPFX/bin` (which is added to the
`$PATH` by default; shims are also a bin-gem-node annex feature).

The ZI command executed will be equivalent to:

```zsh
zi lucid as=null \
    node="remark <- !remark-cli; remark-man; remark-html" \,
    sbin="n:node_modules/.bin/remark" for \
        z-shell/null
```

### `man-only` Profile

Provides the CLI command `remark` with single plugin: Man.

The ZI command executed will be equivalent to:

```zsh
zi lucid as=null \
    node="remark <- !remark-cli; remark-man" \,
    sbin="n:node_modules/.bin/remark" for \
        z-shell/null
```

### `html-only` Profile

Provides the CLI command `remark` with single plugin: Html.

The ZI command executed will be equivalent to:

```zsh
zi lucid as=null \
    node="remark <- !remark-cli; remark-html" \,
    sbin="n:node_modules/.bin/remark" for \
        z-shell/null
```

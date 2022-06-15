<h1 align="center">
  <p><a href="https://github.com/z-shell/zi">
    <img align="center" src="https://github.com/z-shell/zi/raw/main/docs/images/logo.svg" alt="Logo" width="60px" height="60px" /></a>
    ❮ ZI ❯ Package - Remark </p>
</h1>
<h3 align="center">
<table>
    <tr>
        <td><b>Package source:</b></td>
        <td>Tarball</td>
        <td>Git</td>
        <td>Node</td>
        <td>Gem</td>
    </tr>
    <tr>
        <td><b>Status:</b></td>
        <td>➖</td>
        <td>➖</td>
        <td>✔️ (default)</td>
        <td>❌</td>
    </tr>
</table></h3><hr />

## Available `pack''` invocations

```shell
# Download the Node package of remark-cli, remark-man and remark-html
zi pack for remark
```
```shell
# Download the Node package of remark-cli and remark-man
zi pack"man-only" for remark
```
```shell
# Download the Node package of remark-cli and remark-html
zi pack"html-only" for remark
```

### Default Profile

Provides the CLI command `remark` with two plugins: Man and Html.

The Node packages are installed locally into a null-plugin directory (feature of the bin-gem-node annex) and provided to the command line through _shims_, i.e.: automatic forwarder scripts created under `$ZPFX/bin` (which is added to the `$PATH` by default; shims are also a bin-gem-node annex feature).

The ZI command executed will be equivalent to:

```shell
zi lucid as=null \
  node="remark <- !remark-cli; remark-man; remark-html" \
  sbin="n:node_modules/.bin/remark" for \
    z-shell/null
```

### `man-only` Profile

Provides the CLI command `remark` with single plugin: Man.

The ZI command executed will be equivalent to:

```shell
zi lucid as=null \
  node="remark <- !remark-cli; remark-man" \
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

---

> This repository compatible with [ZI](https://github.com/z-shell/zi)

The [remarkjs/remark](https://github.com/remarkjs/remark) zsh package that uses the [zsh-string-lib](https://github.com/z-shell/zsh-string-lib) to automatically:

- get the plugin's Git repository OR release-package URL,
- get the list of the recommended ices for the plugin,
  - there can be multiple lists of ices,
  - the ice lists are stored in _profiles_; there's at least one profile, _default_,
  - the ices can be selectively overridden.

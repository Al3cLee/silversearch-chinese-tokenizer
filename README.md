# Silversearch Chinese Tokenizer

This is a tokenizer plug of [Silversearch](https://github.com/MrMugame/silversearch) for Chinese. It is basically a fork of [this library](https://github.com/LelouchHe/silversearch-chinese-tokenizer) with only one modification: it uses `cut_all` instead of `cut_for_search` of [jieba-wasm](https://github.com/fengkx/jieba-wasm/) for tokenizing; for details, see the README of [jieba-wasm](https://github.com/fengkx/jieba-wasm/) or the [relevant community thread](https://community.silverbullet.md/t/fixing-silver-bullets-chinese-search-gap-a-space-lua-global-search-implementation/3157/16?u=al3clee).

## Install

### 1.

In [Library Manager](https://silverbullet.md/Library%20Manager), click "Install from URI", and enter

```txt
ghr:Al3cLee/silversearch-chinese-tokenizer/PLUG.md
```

It will install the latest release build.

### 1.*

Sometimes the build files fail to fetch into your SilverBullet space. To make sure the install is okay, navigate to `YourSilverBulletSpace/Library/Al3cLee/Silversearch-Chinese-Tokenizer` after installing, and verify whether the files

```txt
- silversearch-chinese-tokenizer.js
- silversearch-chinese-tokenizer.wasm
```

are both there. If not, manually download them there.

### 2.

[Silversearch](https://github.com/MrMugame/silversearch) should also be installed, after install, run the SilverBullet command `Silversearch: Version` to verify your version; if it's `1.2.2` or newer, you are good to go. Then add the below config:

```lua
config.set("silversearch.tokenizers", {
  ["Library/Al3cLee/silversearch-chinese-tokenizer.js"] = {}
})
```

The above code should be inserted as a `space-lua` block in your space, e.g. in your `[[CONFIG]]` page.

### 3.

After this, run `Silversearch: Reindex`.

### Example

For an example of setting this up, please see <https://wentaoli.xyz>. Search for "一些", and then "些", will both return a result, although in Chinese vocabulary "些" is probably not a stand-alone word. If you use the tokenizer by LelouchHe then only "一些" will be found, "些" will not.

# Dependency

Currently, [jieba-wasm](https://github.com/fengkx/jieba-wasm/) is used internally. In rare scenario where it's upgraded to a new version, a reload + reindex is required for best results.

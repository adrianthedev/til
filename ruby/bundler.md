# Bundler

## `nio4r` & `jaro_winkler` errors

First install Xcode then add these

```bash
bundle config build.nio4r --with-cflags="-Wno-incompatible-pointer-types"
bundle config build.jaro_winkler --with-cflags="-Wno-incompatible-pointer-types"
```
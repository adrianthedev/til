# Bundler

## Various gem install problems
### `nio4r` & `jaro_winkler` errors

First install Xcode then add these

```bash
bundle config build.nio4r --with-cflags="-Wno-incompatible-pointer-types"
bundle config build.jaro_winkler --with-cflags="-Wno-incompatible-pointer-types"
```

### `sqlite3` and `mysql`

```bash
gem install jaro_winkler -v 1.5.4 -- --with-cflags="-Wno-incompatible-pointer-types"
brew install mysql mysql-client
bundle config --local build.mysql2 -- --with-mysql-dir=$(brew --prefix mysql-client@8.0)
bundle install
```

### `libxml`

```bash
brew install libxml2
bundle config --global build.libxml-ruby --with-xml2-config="$(brew --prefix libxml2)/bin/xml2-config"
````
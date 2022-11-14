# A good autoloading example

```ruby
require "zeitwerk"
require "listen"
require "concurrent/atomic/read_write_lock"

RELOAD_LOCK = Concurrent::ReadWriteLock.new

loader = Zeitwerk:: Loader.new
loader.push_dir "app"
loader.collapse "app/*"
loader.enable_reloading if ENV[ "RACK_ENV"] = "development"
loader.setup
loader.eager_load if ENV[ "RACK_ENV"] == "production" || ENV[ "CI"]

if ENV[ "RACK_ENV"] = "development"
  listener = Listen.to("app") do
    RELOAD_LOCK.with_write lock do
      loader.reload
    end
  end
  listener.start
end

# in config.ru
run -> (env) do
  RELOAD_LOCK.with_read_lock do
    Router.call(env)
  end
end
```
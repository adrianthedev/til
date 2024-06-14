# Rails

## Redirect www to non-www

```ruby
# https://masilotti.com/rails-redirect-www/
Rails.application.routes.draw do
  match "(*any)",
    to: redirect(subdomain: ""),
    via: :all,
    constraints: { subdomain: "www" }

  # other routes below
end
```
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

## Append inline module to controller

```ruby
Rails.configuration.to_prepare do
  Avo::ApplicationController.include(Module.new {
    def yes = :no
  })
end
```

## Route based authentication

```ruby
class AuthConstraint
  def self.admin? (request)
    cookies = ActionDispatch::Cookies::CookieJar.build(request, request.cookies)

    User.joins(:sessions).where(
      "sessions.id": cookies.signed[:session_id],
      email_address: "youradmin@domain.com"
    ).exists?
  end
end

Rails.application.routes.draw do
  constraints -> (request) { AuthConstraint.admin?(request) } do
    # Any routes you want to protect
  end
end
```
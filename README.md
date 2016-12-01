# ClearSky

My ruby on rails practice from [simple-rails-authentication-with-clearance](https://www.sitepoint.com/simple-rails-authentication-with-clearance/)

```
root to: 'pages#index'

gem 'clearance', '~> 1.11'

rails generate clearance:install
```

Next steps:

1. Configure the mailer to create full URLs in emails:

    # config/environments/{development,test}.rb
    config.action_mailer.default_url_options = { host: 'localhost:3000' }

    In production it should be your app's domain name.

2. Display user session and flashes. For example, in your application layout:

    <% if signed_in? %>
      Signed in as: <%= current_user.email %>
      <%= button_to 'Sign out', sign_out_path, method: :delete %>
    <% else %>
      <%= link_to 'Sign in', sign_in_path %>
    <% end %>

    <div id="flash">
      <% flash.each do |key, value| %>
        <div class="flash <%= key %>"><%= value %></div>
      <% end %>
    </div>

3. Migrate:

    rake db:migrate

*******************************************************************************


rails generate clearance:routes

This command will also set the config.routes setting to false, meaning that custom routes will be used.

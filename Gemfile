source 'https://rubygems.org'

source "https://gem.fury.io/#{ENV.fetch('GEMFURY_USERNAME')}/" do
  gem 'spree', '~> 2.3.4.redbadger'
  gem 'spree_api'
  gem 'spree_backend'
  gem 'spree_cmd', require: false
  gem 'spree_core'
  gem 'spree_frontend'
  gem 'spree_sample'

  gem 'spree_auth_devise', '~> 2.3.0.redbadger'
end

gem 'sqlite3'
gem 'pg'

group :test do
 gem 'require_all'
 gem 'capybara'
 gem 'capybara-screenshot'
 gem 'poltergeist'
end

gemspec

source 'https://rubygems.org'
ruby '2.2.2'

def remove(name)
  @dependencies.reject! { |d| d.name == name }
end

def gem(name, *args)
  remove(name)
  super
end

spec = Bundler.load_gemspec(File.expand_path("../fat_free_crm.gemspec", __FILE__))
spec.runtime_dependencies.each do |dep|
  gem dep.name, *(dep.requirement.as_list)
end

gem 'premailer', require: false

remove 'fat_free_crm'

group :development do
  gem 'quiet_assets'
  gem 'guard'
  gem 'guard-rspec'
  gem 'guard-rails'
  gem 'rb-inotify', require: false
  gem 'rb-fsevent', require: false
  gem 'rb-fchange', require: false
end

# Auto deployment to AWS
group :development do
    gem 'capistrano',         require: false
    gem 'capistrano-rvm',     require: false
    gem 'capistrano-rails',   require: false
    gem 'capistrano-bundler', require: false
    gem 'capistrano3-puma',   require: false
end

group :development, :test do
  gem 'rspec-rails'
  gem 'rspec-activemodel-mocks'
  gem 'headless'
  gem 'byebug'
  gem 'pry-rails' unless ENV["CI"]
  gem 'factory_girl_rails'
end

group :test do
  gem 'capybara'
  gem 'selenium-webdriver'
  gem 'database_cleaner'
  gem "acts_as_fu"
  gem 'zeus' unless ENV["CI"]
  gem 'timecop'
end

gem 'sass-rails'
gem 'coffee-rails'
gem 'uglifier'
gem 'execjs'
gem 'therubyracer', platform: :ruby unless ENV["CI"]
gem 'nokogiri', '>= 1.6.8'
gem 'pg'
gem 'puma'
gem 'sprockets', '3.6.3'

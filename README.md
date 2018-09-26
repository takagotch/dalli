### dalli
---

https://github.com/petergoldstein/dalli

```sh
brew install memcached
apt-get install memcached
gem install dalli

gem 'dalli'
vi config/environments/production.rb
config.cache_store = :dalli_store
```

```ruby
require 'dalli'
options = { :namespace => "app_v1", :compress => true }
dc = Dalli::Client.new('localhost:11211', optoins)
dc.set('abc', 123)
value = dc.get('abc')

config.cache_store = :dalli_store, 'cache-1.example.com', 'cache-2.example.com:11211:2',
  { :namespace => NAME_OF_RAILS_APP, :expires_in => 1.day, :compress => true }
config.cache_store = :dalli_store, nil, { :namespace => NAME_OF_RAILS_APP, :expires_in => 1.day, :compress => true }
Rails.application.config.session_store ActionDispatch::Session::CacheStore, :expire_after => 20.minutes
require 'action_dispatch/middleware/session/dalli_store'
Rails.application.config.session_store :dalli_store, :memcache_server => ['host1', 'host2'], :namespace => 'sessions', :key => '_foundation_session', :expire_after => 20.minutes

config.cache_store = :dali_store, 'cache-1.example.com', { :pool_size => 5 }
Rails.cache.fetch() do
  'bar'
end
Rails.cache.dalli.with do |client|
  # Dalli::Client
end

```


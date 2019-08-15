# capistrano-shoryuken
Shoryuken integration for Capistrano.  Loosely based on `capistrano-sidekiq`

## Installation

Add this line to your application's Gemfile:

    gem 'capistrano-shoryuken', github: 'interfolio/capistrano-shoryuken'

or:

    gem 'capistrano-shoryuken', group: :development

And then execute:

    $ bundle


## Usage
```ruby
    # Capfile

    require 'capistrano/shoryuken'
```


Configurable options, shown here with defaults (using Capistrano 3 syntax):

```ruby
    # config/deploy.rb
    
    # Whether or not to hook into the default deployment recipe.
    set :shoryuken_default_hooks,  true
    
    set :shoryuken_pid,            -> { File.join(shared_path, 'tmp', 'pids', 'shoryuken.pid') }
    set :shoryuken_env,            -> { fetch(:rack_env, fetch(:rails_env, fetch(:stage))) }
    set :shoryuken_log,            -> { File.join(shared_path, 'log', 'shoryuken.log') }
    set :shoryuken_config,         -> { File.join(release_path, 'config', 'shoryuken.yml') }
    set :shoryuken_requires,       -> { [] }
    set :shoryuken_options,        -> { ['--rails'] }
    set :shoryuken_queues,         -> { [] }
    set :shoryuken_role,           :app
```

## Changelog
- 0.1.6: Fix capistrano warning for previously invoked shoryuken:stop
- 0.1.5: Bug fix when using Capistrano 2
- 0.1.4: Minimum ruby 1.9.2
- 0.1.3: Fix erroneous auto-loading from Bundler.require
- 0.1.2: Support --require option.
- 0.1.1: Default --rails option. Support Capistrano 3
- 0.1.0: Support Capistrano 2

## Contributors

- [Interfolio] (https://github.com/interfolio)

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

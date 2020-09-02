# Animikii Rubocop

An attempt at standardizing how we write code across all team members and projects. 

**!!! IMPORTANT**

Whenever we add new rules to `.rubocop.yml` we should bump the version tag so that existing projects don't recieve new rules and thus break...

Just create a new release and use the version in your `.rubocop.yml` `inherit_from:` url

# Install

Add to your `Gemfile` and bundle

```ruby
group :development, :test do
  gem 'rubocop-performance', require: false
  gem 'rubocop-rails', require: false
end
```

# Setup

You don't need much to set this up now in `.rubocop.yml`

```yaml
---
inherit_from:
  - https://raw.githubusercontent.com/animikii/rubocop-akii/v1.0/.rubocop.yml

require:
  - rubocop-performance
  - rubocop-rails
```

# Usage

### Check

```bash
bundle exec rubocop
```

### Autocorrect

```bash
bundle exec rubocop -a
```

### Generate `rubocop_todo.yml`

```bash
bundle exec rubocop --auto-gen-config
```

### Travis

Create a script in `bin/travis-rubocop.sh` and add

```bash
#!/usr/bin/env bash
travis_fold start "rubocop"

echo "Running Rubocop"

bundle exec rubocop

travis_fold end "rubocop"
```

Then import `travis_fold` and execute the script in `.travis.yml`

```yaml
before_script:
  - export -f travis_fold
script:
  - ./bin/travis-rubocop.sh
```

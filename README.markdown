# Animikii Rubocop

An attempt at standardizing how we write code across all team members and projects. 

# Making Changes

1. Propose - create a pull request proposing a change to the Rubocop rule(s) and request everyone to review it
2. Discuss - argue, gloves come off, create alliances
3. Vote - upvote/downvote with emojis 👍/👎 😍/🤮 
4. Merge - merge the pull request and create a new release with a version bump

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

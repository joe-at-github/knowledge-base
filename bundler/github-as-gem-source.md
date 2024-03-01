# Github as a gem source

Typically, you would require gems in a Ruby project using a `Gemfile` like this:

```ruby
# Gemfile

source 'https://rubygems.org'

gem 'some_gem'
```

You can also bundle install a gem hosted on your Github account but not yet published to RubyGems.

# Here is how to do it

## Edit your `Gemfile`
```ruby
gem 'some_gem', git: 'https://github.com/<your-github-user-name>/some_gem'
```

## Generate a Personal Access Token (PAT)
GitHub has made changes to its authentication methods, and as of August 13, 2021, it no longer accepts account passwords for Git operations. Instead, you’ll need to use a Personal Access Token (PAT) for authentication.

When running `bundle install`, you will be prompted for your github username and password.
Instead of a password, you will need to type your PAT.

To create a Personal Access Token (PAT) on GitHub:
- Log in to your GitHub account.
- Go to Settings → Developer Settings → Personal Access Token.
- Click on Generate New Token.
- Provide a note (for your reference) and select the necessary access scopes.
- Click Generate Token and copy the generated token (it will look something like `ghp_sFhFsSHhTzMDreGRLjmks4Tzuzgthdvfsrta`).

## Run `bundle install`
When prompted, type in your github username and PAT for this project.
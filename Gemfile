# frozen_string_literal: true

source "https://rubygems.org"

gem 'jekyll'
gem 'github-pages'

group :jekyll_plugins do
  gem "jekyll-remote-theme"
  gem "jekyll-paginate"
  gem "rake"
end

require 'rbconfig'
gem 'wdm', '>= 0.1.0' if RbConfig::CONFIG['target_os'] =~ /mswin|mingw/i

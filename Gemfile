# frozen_string_literal: true

source "https://rubygems.org"

# Specify the gem's dependencies in jekyll-admin.gemspec
# gemspec

gem "jekyll-theme-chirpy", "~> 5.2", ">= 5.2.1"

group :test do
  gem "html-proofer", "~> 3.18"
end

# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
install_if -> { RUBY_PLATFORM =~ %r!mingw|mswin|java! } do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :install_if => Gem.win_platform?

# Jekyll <= 4.2.0 compatibility with Ruby 3.0
gem "webrick", "~> 1.7"

# To allow testing with specific Jekyll versions
gem "jekyll", ENV["JEKYLL_VERSION"] if ENV["JEKYLL_VERSION"]
gem "kramdown-parser-gfm" if ENV["JEKYLL_VERSION"] == "~> 3.9"

# Fixture site dependencies
gem "jekyll-redirect-from"


gem "jekyll"
# gem 'jekyll-admin'
gem 'jekyll-admin', group: :jekyll_plugins
gem "jekyll-gist"
gem "jekyll-coffeescript"
# gem "jekyll-seo-tag", "~> 1.5"
# gem "some-other-jekyll-plugin"
# Site dependencies
gem "jekyll-seo-tag"
gem "jekyll-sitemap"
# gem "jekyll-mermaid"

# A dependency of a custom-plugin inside `_plugins` directory.
gem "nokogiri", "~> 1.11"
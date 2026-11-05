source "https://rubygems.org"

gem "jekyll", "~> 4.3.0"

# Jekyll 4.3 dependencies no longer included as default gems in Ruby 3.4.
gem "csv"
gem "base64"
gem "bigdecimal"

gem "wdm", "~> 0.1.0" if Gem.win_platform?
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-sitemap"
  gem "jekyll-sass-converter", "~> 2.0"
  gem "jekyll-paginate"
  gem "jekyll-gist"
  gem "jekyll-seo-tag"
  gem "jekyll-redirect-from"
end

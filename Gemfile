source "https://rubygems.org"

gem 'dotenv'
gem 'html-proofer'
gem 'rake'

group :development do
  gem 's3_website'
end

# Use preinstalled Gem version in CI
group :ci, optional: true do
  gem 's3_website', path: '/usr/local/bundle/gems/s3_website-3.4.0'
end


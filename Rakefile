require 'html-proofer'
require 'dotenv/tasks'

# Deploy. Depends on the build and s3_push tasks
desc 'it deploys the site with current posts'
task :deploy do
  Rake::Task['build'].invoke
  Rake::Task['s3_push'].invoke
end

### BUILD
desc 'it builds the site with current posts'
task :build do
  sh 'hugo'
end

### S3_PUSH
desc 'it pushes the generated site to s3 and Cloudfront'
task s3_push: :dotenv do
  sh "bundle exec s3_website push"
end

### HTML_PROOF
desc 'it checks validity of the generated HTML'
task :html_proof do
  Rake::Task['build'].invoke
  options = { :assume_extension   => true,
              :http_status_ignore => [999],
              :internal_domains   => ['flyinggrizzly.io',
                                      'www.flyinggrizzly.io'] }
  HTMLProofer.check_directory("./_site", options).run
end

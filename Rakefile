require 'dotenv'
Dotenv.load

task :default => :deploy

desc 'Clean up generated site'
task :clean do
  sh 'rm -rf _site'
end

desc 'Buil up generated site'
task :build do
  sh 'jekyll build'
end

namespace :production do

  desc 'deploy to production'
  task :deploy => [:build, :sync, :clean] do
  end

  task :sync do
    puts 'syncing files'
    sh 'rsync -aP --delete-after --remove-source-files _site/ /var/www'
  end
end

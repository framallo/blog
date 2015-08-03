task :default => :deploy

desc 'build and deploy in production'
task :deploy => [:build, :sync, :clean] do
end

task :sync do
  puts 'syncing files'
  sh 'rsync -aP --delete-after _site/ /var/www'
end

desc 'Clean up generated site'
task :clean do
  sh 'rm -rf _site'
end

desc 'Buil up generated site'
task :build do
  sh 'jekyll build'
end

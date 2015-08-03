
task :default => :deploy

desc 'deploy to production'
task :deploy do
  sh 'jekyll build'
  puts 'deploying to production server'
  sh 'rsync -aP _site/ blog:/var/www/'
end

desc 'Clean up generated site'
task :clean do
  sh 'rm -rf _site'
end

desc 'Buil up generated site'
task :Build do
  sh 'jekyll build'
end

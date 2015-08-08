task :default => :build

desc 'Build up generated site'
task :build do
  sh 'jekyll build'
end

desc 'serve site for development'
task :serve do
  sh 'jekyll serve -w'
end

namespace :production do

  desc 'build and deploy in production'
  task :deploy => [:build, :sync, :clean] do
  end

  desc 'Build up generated site'
  task :build do
    sh 'jekyll build --config _config.yml,_config_production.yml'
  end

  task :sync do
    puts 'syncing files'
    sh 'rsync rsync -aP --fuzzy -z --checksum --itemize-changes _site/ /var/www'
  end

  desc 'Clean up generated site'
  task :clean do
    sh 'rm -rf _site'
  end

end

namespace :rsync do

  desc 'build locally, then deploy to staging with rsync'
  task :deploy_to_staging do
    sh 'jekyll build --config _config.yml,_config_staging.yml'
    sh 'rsync -aP --fuzzy -z --checksum --itemize-changes _site/ blog:/var/www/staging/'
  end

  desc 'build locally, then deploy to production with rsync'
  task :deploy_to_production do
    sh 'jekyll build --config _config.yml'
    sh 'rsync -aP --fuzzy -z --checksum --itemize-changes _site/ blog:/var/www/'
  end
end

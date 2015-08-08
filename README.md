# Federico Ramallo Blog

This blog generates my website http://framallo.com/ and is based on the [Lanyon theme](http://lanyon.getpoole.com/)

# Build the website

run `jekyll build`

# Building and deploying

I use rake. This are the tasks available

    rake build                       # Build up generated site
    rake production:build            # Build up generated site
    rake production:clean            # Clean up generated site
    rake production:deploy           # build and deploy in production
    rake rsync:deploy_to_production  # build locally, then deploy to production with rsync
    rake rsync:deploy_to_staging     # build locally, then deploy to staging with rsync
    rake serve                       # serve site for development

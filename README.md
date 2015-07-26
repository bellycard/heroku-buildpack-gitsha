# Heroku pre-deploy buildpack

Add the following to a `.buildpacks` file in our root directory:

```
https://github.com/bellycard/heroku-buildpack.git
https://github.com/heroku/heroku-buildpack-ruby.git
```

## GITSHA

This buildpack will include a new `.gitsha` file containing the git revesion and make this available to napa's `/health` endpoint

# Heroku pre-deploy buildpack (GITSHA)

## Prerequisite (Napa services only)

`bundle update --source napa`


There are a couple of ways of utilizing multiple buildpacks on Heroku.
David Dollar has a convenient [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi),
which looks at a `.buildpacks` file to download, execute, and continue through each buildpack
defined in `.buildpacks`. This file clearly defines all the buildpacks and their order; therefore,
I will suggest this method over the CLI method described later:

## Enable with ddollar/heroku-buildpack-multi

### 1) Enable multiple buildpacks:

`heroku buildpacks:set https://github.com/ddollar/heroku-buildpack-multi.git`


### 2) Add this gitsha buildpack

Add the following to a `.buildpacks` file in our root directory:

```
https://github.com/bellycard/heroku-buildpack-gitsha.git
https://github.com/heroku/heroku-buildpack-ruby.git
```


## Enable with Heroku's CLI (Alternative setup)

Please refer to [this article on heroku](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app)


### 1) Add the buildpacks via Heroku CLI

```
heroku buildpacks:set https://github.com/heroku/heroku-buildpack-ruby
heroku buildpacks:add --index 1 https://github.com/bellycard/heroku-buildpack-gitsha.git
```

### 2) Verify buildpacks

`heroku buildpacks`

NOTE: If you wantt to switch from this method to using ddollar's [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi), you will need to clear the existing buildpacks:

`heroku buildpacks:clear`


## GITSHA

This buildpack will include a new `.gitsha` file containing the git revesion

If you are using [napa](https://github.com/bellycard/napa), this will be available to the `/health` endpoint

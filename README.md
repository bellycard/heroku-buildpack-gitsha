# Heroku buildpack for git sha output for use in napa

Using [napa](https://github.com/bellycard/napa) and Heroku? Want to have the `/health`
display the gitsha of the current slug?

Add the following to a `.buildpacks` file in our root directory:

```
https://github.com/ashtonthomas/heroku-buildpack-metadata.git
https://github.com/heroku/heroku-buildpack-ruby.git
```


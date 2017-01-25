# Deploy Mattermost Team or Enterprise Edition to Heroku

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

This buildpack is an [inline buildpack](https://github.com/kr/heroku-buildpack-inline/) (tldr: this repo deploys to Heroku and uses itself as a buildpack) for deploying [Mattermost](https://mattermost.org) to [Heroku](https://heroku.com).
It must used in tandem with [This customized Nginx Buildpack](https://github.com/cadecairos/nginx-buildpack).

Mattermost is not a [12 factor compatible app](http://12factor.net/config), so the startup script writes your Heroku environment variables to a config file when the dyno starts.

### Known to work with Mattermost 3.6.0 Team and Enterprise editions

## Configuration options

### Buildpack Specific Variables

Set `MATTERMOST_VERSION` to the release version you'd like to install. i.e. '3.6.0'
Set `MATTERMOST_TYPE` to either 'team' or 'enterprise'

### Mattermost Configuration

Mattermost-Heroku supports most configuration options that Mattermost 3.6.0 offers. You can see the mapping between Mattermost config settings and Heroku environment variables in the [configuration template](/config/config-heroku-template.json).

 [Check out the Mattermost configuration documentation for detailed information about each option.](https://docs.mattermost.com/administration/config-settings.html)

## Rebuilding

Use the deploy menu on the Heroku dashboard to trigger manual deploys.

## Warnings

1. Don't make configuration changes in the Mattermost admin console.
   Any configuration changes in the Mattermost admin console will likely be lost on dyno restart (which may be every 24 hours) and will likely not be distributed across multiple dynos.
2. Not using s3 means any uploads will be lost on dyno restart or application reconfiguration or redeploy and won't be consistent across multiple dynos.
   Without s3 backing this is not anything more than a one time demo.

## Enterprise Edition
Activate it as instructed in the docs https://docs.mattermost.com/install/ee-install.html

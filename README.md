# [Backstage](https://backstage.io)

This is a scaffolded Backstage App, Good Luck!

## setup 

Set env vars:

```
TMPDIR={a directory writable by docker (limited under limactl)}

BACKSTAGE_GITHUB_TOKEN=ghp_fillMeIn

DOCKER_HOST={docker host path like unix:///Users/ross.bob/.lima/docker/sock/docker.sock}
```

> Note for `DOCKER_HOST`, at least on my machine the env var is important.  Using a docker context does not work.
> The `DOCKER_HOST` needs access to TMP space
> For `TMPDIR` I'm using the full path to this repo's tmp directory

See [setting up github integration](https://backstage.io/docs/getting-started/config/authentication#setting-up-a-github-integration) for info on token.

You also need to [create a Github OAUTH app.](https://backstage.io/docs/auth/github/provider/#create-an-oauth-app-on-github)  


#### For Github 
See [setting up github integration](https://backstage.io/docs/getting-started/config/authentication#setting-up-a-github-integration) for info on token. In short it needs at least `repo` and `workflow` permissions.

Next we [need a github oauth app](https://backstage.io/docs/auth/github/provider/).  Settings -> Developer -> Oauth apps -> New Oauth app.

Update or create app.config.local.yaml.  This one is used for user authentication.  Use the clientId and secret from the github oauth app.


Update or create `app.config.local.yaml` (don't worry it's .gitignore'd).  This one is used for user authentication.
Use the following config:

* Application name: Backstage (or your custom app name)
* Homepage URL: http://localhost:3000
* Authorization callback URL: http://localhost:7007/api/auth/github/handler/frame


```yaml
auth:
  # see https://backstage.io/docs/auth/ to learn about auth providers
  environment: development
  providers:
    # See https://backstage.io/docs/auth/guest/provider
    guest: {}
    github:
      development:
        clientId: FILL ME
        clientSecret: FILL ME
```

To add a github user update `org.yaml` with your github username:
https://backstage.io/docs/getting-started/config/authentication#adding-a-user


To start the app, run:

```sh
yarn install
yarn dev
```

Visit http://localhost:3000


Import a sample "component".  A component is like a repo or service.

- Go to Catalog -> click 'Create' -> Register existing component
- Paste in `https://github.com/tgaff-mfw/jetbrains_sample_rails_app/blob/master/catalog-info.yaml`
- Import and you should be able to view its docs.

To add a github user, update `org.yaml` with your username:
https://backstage.io/docs/getting-started/config/authentication#adding-a-user
(Note this is because we're not using a Org entity provider for dev)


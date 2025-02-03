# [Backstage](https://backstage.io)

This is a scaffolded Backstage App, Good Luck!

## setup 

Set env vars:
```
TMPDIR={a directory writable by docker (limited under limactl)}

BACKSTAGE_GITHUB_TOKEN=ghp_fillMeIn
```
See [setting up github integration](https://backstage.io/docs/getting-started/config/authentication#setting-up-a-github-integration) for info on token. In short it needs at least `repo` and `workflow` permissions.

Update or create app.config.local.yaml.  This one is used for user authentication.

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

Import a sample "component".  A component is like a repo or service.

Go to Catalog -> click 'Create' -> Register existing component
Paste in `https://github.com/tgaff-mfw/jetbrains_sample_rails_app/blob/master/catalog-info.yaml`
Import and you can view its docs.

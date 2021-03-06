# OAuth2/Phoenix Example Application

> This is an example application showing how one can integrate with the
> [OAuth2](https://github.com/scrogson/oauth2) library and
> the [Phoenix](https://github.com/phoenixframework/phoenix) framework.

![Alt text](https://monosnap.com/file/PahR5zCiU9EapeRyuvAKn1AyTitp1p.png)

To start the application:

1. Register a new application with [Fitbit](https://dev.fitbit.com/apps)
    - Choose 'Client' for OAuth 2.0 Application Type
    - Enter http://lvh.me:4000/auth/callback for the Authorization callback URL
    - Choose 'Read-Only' for Default Access Type
2. Set the `REDIRECT_URI` environment variable to the callback URL
3. Set the `CLIENT_ID` and `CLIENT_SECRET` environment variables
4. Install Elixir dependencies with `mix deps.get`
5. Install NodeJS dependencies with `npm install`
6. Start Phoenix router with `mix phoenix.server`

Now you can visit `lvh.me:4000` from your browser and click "Sign in with
Fitbit".

After authorizing the application, you should see the welcome message above.

To revoke access, clear any browser cookies and visit
https://www.fitbit.com/user/profile/apps

To deploy the app to Heroku:

1. Create and configure the heroku app:

```
$ heroku create
$ heroku buildpacks:set https://github.com/gjaldon/phoenix-static-buildpack
$ heroku buildpacks:add --index 1 https://github.com/HashNuke/heroku-buildpack-elixir
$ heroku addons:create heroku-postgresql
$ heroku config:set SECRET_KEY_BASE=[long random string]
$ heroku config:set CLIENT_ID=[your fitbit client id]
$ heroku config:set CLIENT_SECRET=[your fitbit client secret]
$ heroku config:set REDIRECT_URI=https://your-app-name.herokuapp.com/auth/callback
```
Return to [Fitbit](https://dev.fitbit.com/apps) and edit your application's configuration.  Add the new redirect uri.

Note:  if you cloned this repository from github.com/wsmoak it
defaults to the fitbit-heroku branch.

You will need to push to heroku like so:

$ git push heroku fitbit-heroku:master


References
* https://wiki.fitbit.com/display/API/OAuth+2.0
* https://community.fitbit.com/t5/Web-API/bd-p/dev
* http://maxwellholder.com/blog/build-a-blog-with-phoenix-and-ember
* See https://devcenter.heroku.com/articles/git#deploying-code

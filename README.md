# A [Hubot](https://github.com/github/hubot) adapter for [Flowdock](https://www.flowdock.com)

[Flowdock](https://www.flowdock.com/) is a web based collabration and chat app. It integrates nicely with GitHub, Pivotal Tracker, Twitter, JIRA, Confluence, most CI systems and even email.

You should report any issues or submit any pull requests to the
[Flowdock adapter](https://github.com/flowdock/hubot-flowdock) repository.

## Compatibility with Hubot

 * 0.6.x => Hubot >=2.5.0
 * 0.5.x => Hubot >=2.4.8
 * 0.4.x => Hubot 2.4.2 - 2.4.8
 * 0.3.x => Hubot 2.3.x
 * 0.2.5 => Hubot 2.2.x

## Compatibility with NodeJS

 * Preferably use NodeJS 0.8.x or later

## Getting Started

First, create your own hubot template by using [the getting started instructions](https://github.com/github/hubot/blob/master/docs/README.md) of the hubot repository.

Then you will need to edit the `package.json` for your hubot and add the
`hubot-flowdock` adapter dependency.

    "dependencies": {
      "hubot-flowdock": ">= 0.0.1",
      "hubot": ">= 2.0.0",
      ...
    }

Then save the file, and commit the changes to your hubot's git repository.

If deploying to Heroku you will need to edit the `Procfile` and change the
`-a campfire` option to `-a flowdock`. Or if you're deploying locally
you will need to use `-a flowdock` when running your hubot.

### Bot name

Note that by default, hubot will think its name is "Hubot" and will only respond to that name. You can configure what name hubot thinks it has, with environment variable HUBOT_NAME or with the `-n` flag when starting the bot. Note that you will run into problems if the name that hubot internally uses is different from the actual display name of the user that hubot uses to connect to Flowdock with. The Flowdock adapter will however try to mitigate the effects of wrong name, but you should still configure it properly.

## Configuring the Adapter

The Flowdock adapter requires either a user's personal api token (obtainable from [Flowdock account page](https://www.flowdock.com/account/tokens)) as environment variable

    HUBOT_FLOWDOCK_API_TOKEN

or a user's email and password as environment variables:

    HUBOT_FLOWDOCK_LOGIN_EMAIL
    HUBOT_FLOWDOCK_LOGIN_PASSWORD

    # Heroku specific: to enable the keep-alive functionality for Hubot > 2.1.4.
    # More info at https://github.com/github/hubot/pull/270.
    HEROKU_URL

### Name

Remember to set the bot's name to match the Flowdock login's display name. See "Bot name" above. You will see warnings in the logs when starting hubot if the name does not match the Flowdock login.

### Flowdock Login Email

This is the email address of the account which your hubot will be using.

### Flowdock Login Password

This is the password of the account which your hubot will be using. Note: if you use third party authentication (e.g. Google), you need to [set a password for your account manually](https://www.flowdock.com/account/authorizations).

### Heroku Hostname

Your Hubot instance's hostname in Heroku.

### Configuring the variables on Heroku

    % heroku config:add HUBOT_FLOWDOCK_LOGIN_EMAIL="..."

    % heroku config:add HUBOT_FLOWDOCK_LOGIN_PASSWORD="..."

### Configuring the variables on UNIX

    % export HUBOT_FLOWDOCK_LOGIN_EMAIL="..."

    % export HUBOT_FLOWDOCK_LOGIN_PASSWORD="..."

## API

### Flows

If you need to access data about flows, you can find them in `robot.adapter.flows`.

### Comments vs. normal messages

By default hubot will always respond to the same thread that the message that caused the response was in. In scripts you can override this by setting `msg.envelope.newMessage = true`.

## License

MIT

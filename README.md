# jargonbot

Jargonbot is a tool for seamlessly synergizing your Slack communications. When it hears a term from 
an array of business buzzwords, it responds with a random string of streamlined collaborative insights. For example:

```
james> yeah let's sync up later
jargonbot> assertively optimize best-of-breed stakeholders
```

You can adjust the collection of trigger words by adding or removing terms from [this list](https://github.com/jtotoole/jargonbot/blob/master/scripts/jargonbot.coffee#L66).

Original script from [Tim Hopper](https://github.com/tdhopper); documentation adapted from [Michi Kono](https://github.com/michikono/slackbot-tutorial).

## Setup

If you've already got Hubot configured, simply add [jargonbot.coffee](https://github.com/jtotoole/jargonbot/blob/master/scripts/jargonbot.coffee) to your scripts folder. If not, clone this repo and follow the instructions below.

jargonbot is built on the [Hubot][hubot] framework. It was
initially generated by [generator-hubot][generator-hubot], and configured to be
deployed on Heroku to get you up and running as quick as possible.

[hubot]: http://hubot.github.com
[generator-hubot]: https://github.com/github/generator-hubot

## Testing the bot locally

    HUBOT_SLACK_TOKEN=YOUR_TOKEN_HERE ./bin/hubot -a slack

You'll see some start up output and a prompt:

    [Sat Feb 28 2015 12:38:27 GMT+0000 (GMT)] INFO Using default redis on localhost:6379
    jargonbot>

## Deployment

This is a modified set of instructions based on the [instructions on the Hubot wiki](https://github.com/github/hubot/blob/master/docs/deploying/heroku.md).

- Follow the instructions above to create a hubot locally
- Install [heroku toolbelt](https://toolbelt.heroku.com/) if you haven't already.
- `heroku create my-company-slackbot`
- `heroku addons:add redistogo:nano`
- Activate the Hubot service on your ["Team Services"](http://my.slack.com/services/new/hubot) page inside Slack.
- Add the [config variables](#adapter-configuration). For example:

        % heroku config:add HUBOT_SLACK_TOKEN=xoxb-1234-5678-91011-00e4dd
        % heroku config:add HEROKU_URL=http://my-company-slackbot.herokuapp.com

- Deploy and start the bot:

        % git push heroku master
        % heroku ps:scale web=1

- Profit!

## Configuration

This adapter uses the following environment variables:

 - `HUBOT_SLACK_TOKEN` - this is the API token for the Slack user under which you'd like to run jargonbot.

To add or remove jargonbot from specific channels or private groups, you can use the /kick and /invite slash commands that are built into Slack.

## Deployment

    % heroku create --stack cedar
    % git push heroku master

If you run into any problems, checkout Heroku's [docs][heroku-node-docs].

More detailed documentation can be found on the [deploying hubot onto
Heroku][deploy-heroku] wiki page.

[heroku-node-docs]: http://devcenter.heroku.com/articles/node-js
[deploy-heroku]: https://github.com/github/hubot/blob/master/docs/deploying/heroku.md

## Adapters

Jargonbot is configured by default for Slack. Adapters are also available for a number of other
chat services -- check [Hubot Adapters][hubot-adapters] to see all available.

[hubot-adapters]: https://github.com/github/hubot/blob/master/docs/adapters.md

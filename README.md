![PointsThing Banner](https://github.com/ServiceNowDevProgram/Points-Thing/assets/31702109/6218d037-81ee-4c5d-aa26-c745a7297cf4)

This bot is what controls the @Points-Thing bot on the sndevs.com workspace.

## What is Points-Thing?

On the SNDevs workspace, we like to give kudos to each other! Especially when someone has been particularly helpful (answered a ServiceNow question, helped review a code snippet, or simply pointed to the right documentation) or even when someone provided a much needed laugh (a funny joke, a well-timed meme, or simple relatable musings).

To give those kudos, we made the Points-Thing bot! Simply @ mention someone and put ++ right after to give them a point.

`@AbelTuter ++`

And the bot keeps track (via a ServiceNow instance) of how helpful that person has been. Now user can quickly see who in the community has been a great contributor. And contributors have a way to show credibility in their responses.

The bot evolved from there and functionality has been added onto it ever since it was created in 2017.



🔔🔔🔔<br>
***CONTRIBUTORS must follow all guidelines in [CONTRIBUTING.md](CONTRIBUTING.md)*** or run the risk of having your Pull Requests labeled as spam.<br>
🔔🔔🔔

## To set up:

1. Fork this repo
2. Go to your ServiceNow instance
3. Go to `System Applications` => `Studio`
4. Once Studio loads, select `Import From Source Control`
5. Use your forked repo to [Import your application](https://developer.servicenow.com/dev.do#!/learn/learning-plans/tokyo/new_to_servicenow/app_store_learnv2_devenvironment_tokyo_importing_an_application_from_source_control)
6. See below on how to get this bot working on your own server
7. Make updates to the application (see [CONTRIBUTING.md](CONTRIBUTING.md) for additional details)
8. In Studio, commit your changes to source control
9. Submit a pull request to the ServiceNowDevProgram/Points-Thing `main` branch

An accepted Pull Request and merge does not necessarily mean the functionality will go live immediately, as an admin for the host instance will need to pull the application into ServiceNow.

## Installing this bot on your own Slack server

### Create App, Install into your workspace

#### Via a Manifest

* Create a new app, select "From an app manifest"
* Select the workspace into which you want to install this app
* Copy and paste the manifest from either [appmanifest.json](https://github.com/ServiceNowDevProgram/Points-Thing/blob/18dcc148d7564eca0048a0fc1aef63f2a69cce24/Slack%20App%20Manifest/appmanifest.json) or [appmanifest.yaml](https://github.com/ServiceNowDevProgram/Points-Thing/blob/18dcc148d7564eca0048a0fc1aef63f2a69cce24/Slack%20App%20Manifest/appmanifest.yaml)
* Create the app
* Navigate to `Features` > `Event Subscriptions`
* Populate the `Request URL` with: https://YOURDEVINSTANCE.service-now.com/api/x_snc_pointsthing/points_thing
> `When you tab out of the field, make sure the URL is "Verified" before you proceed.`
* Navigate to `Settings` > `Install App`
* Click the `Install to Workspace` button
* Verify the `view` and `do` permissions
* Click the `Allow` button
* Copy the `Bot User OAuth Token` for the ServiceNow system property configuration later

#### Manually

* Create a new app, select "From scratch"
* Select the workspace into which you want to install this app
* Navigate to `Features` > `Event Subscriptions`
* Turn on `Enable Events`
* Populate the `Request URL` with: https://YOURDEVINSTANCE.service-now.com/api/x_snc_pointsthing/points_thing
> `When you tab out of the field, make sure the URL is "Verified" before you proceed.`
* Expand the `Subscribe to bot events` section
* Click the `Add bot User Event` button
* Search for and select `message.channels`
* Search for and select `message.groups`
* Click the `Save Changes` button
* Navigate to `Features` > `OAuth & Permissions`
* Scroll down to `Bot Token Scopes`
* Click the `Add an OAuth Scope` button
* Search for and select `chat:write`
* Navigate to `Settings` > `Install App`
* Click the `Install to Workspace` button
* Verify the `view` and `do` permissions
* Click the `Allow` button
* Copy the `Bot User OAuth Token` for the ServiceNow system property configuration later

### Connect them together

* Create a global property called "pointsthing.token" and place your bot token in this property.

### Testing

* Invite your bot to a channel
* @ mention someone in your server with a ++, eg. `@Earl Duque ++`

### Troubleshooting

* Check the Payload `x_snc_pointsthing_payload` table to make sure SN is receiving messages
* Check 'Outbound HTTP Requests' to make sure the bot is replying to the channel

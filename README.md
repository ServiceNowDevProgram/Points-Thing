# Points-Thing

This bot is what controls the @Points-Thing bot on the sndevs.com slack workspace.

🔔🔔🔔<br>
***CONTRIBUTORS must follow all guidelines in [CONTRIBUTING.md](CONTRIBUTING.md)*** or run the risk of having your Pull Requests labeled as spam.<br>
🔔🔔🔔

## To set up:

1. Fork this repo
2. Go to your ServiceNow instance
3. Go to `System Applications` => `Studio`
4. Once Studio loads, select `Import From Source Control`
5. Use your forked repo to [Import your application](https://developer.servicenow.com/dev.do#!/learn/learning-plans/quebec/new_to_servicenow/app_store_learnv2_devenvironment_quebec_importing_an_application_from_source_control)
6. See below on how to get this bot working on your own slack server
7. Make updates to the application (see [CONTRIBUTING.md](CONTRIBUTING.md) for additional details)
8. In Studio, commit your changes to source control
9. Submit a pull request to the ServiceNowDevProgram/Points-Thing `main` branch

An accepted Pull Request and merge does not necessarily mean the functionality will go live immediately, as an admin for the host instance will need to pull the application into ServiceNow.

## Installing this bot on your own Slack server

### Create Slack App, Install into Slack

#### Via a Manifest

* Create a new app, select "From an app manifest"
* Select the Slack Workspace into which you want to install this app
* Copy and paste the manifest from either [appmanifest.json](Points-Thing/appmanifest.json) or [appmanifest.yaml](Points-Thing/appmanifest.yaml)
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
* Select the Slack Workspace into which you want to install this app
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

* Invite your bot to a Slack channel
* @ mention someone in your server with a ++, eg. `@Earl Duque ++`

### Troubleshooting

* Check the Payload `x_snc_pointsthing_payload` table to make sure SN is receiving Slack messages
* Check 'Outbound HTTP Requests' to make sure the bot is replying to the channel

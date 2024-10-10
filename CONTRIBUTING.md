# Contributing

## General requirements

- Pull request descriptions must be explicit and descriptive to what is being changed.
  - Changes that are not within the scope of the description will result in the entire PR being rejected
- No updates should be made directly to the automatically generated ServiceNow folders. Updates to these files should be done via the [Regular method](README.md#manually) described on the readme.
- Low effort/spam Pull Requests will be marked as spam accordingly.
- Filenames should not have special characters that are not allowed on normal file systems (eg. do not put ! in the file name).


## Messages

To contribute new messages for when points are awarded or milestones are reached:
1. Fork this repo and import it into your instance
2. In your instance navigate to `Points Thing > Messages`
3. Add an entry
4. In Studio, commit your changes to source control
5. Submit a pull request to the ServiceNowDevProgram/Points-Thing main branch

### To create a new message

There are three fields to fill in, Message, Point Trigger, and Send to milestone channel.

#### Message

In the Message field create the string that is the message you want to be sent followed by a semicolon. 
There are placeholders available for system generated values:

- `user`: the @user name that recieved the points
- `points`: the new number of points that the user has (90 day running total)
- `total`: the actual all time total number of points the user has

An example of a good message would be:
`'Congrats ' + user + ' you now have ' + points + ' points';`

Note: Any message that is NOT sent to the milestone channel will have `'(' + total + ' total)'` automatically appended to it.

You can also use emojis in your message by including them with the standard :emojiName: notation that slack uses. 


#### Point Trigger

This is an optional field. If filled in, the message will only trigger at this number of lifetime total points.
If blank it will trigger for any number of points that does not have a specific trigger (i.e. if there is a special message for 100 points, that message will trigger and not the blank one).
If there are multiple messages that have the same trigger value (including blank) the message that will trigger will be randomly chosen.

#### Send to milestone channel

If this is selected than the message will be sent to the defined Milestone channel in addition to the standard reply. This will also suppress the `'(' + total + ' total)'` that gets appended to most messages.


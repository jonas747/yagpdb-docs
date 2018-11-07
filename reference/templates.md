# Templates

{% hint style="warning" %}
Put curly brackets around the templates like this: **`{{.User.Username}}`**
{% endhint %}

{% hint style="info" %}
If you want to put a template inside a template \(e.g. to wrap toString in joinStr around .Guild.MemberCount\), you use normal braces:  
`{{joinStr "" "Our member count is " (toString .Guild.MemberCount) "!"}}`
{% endhint %}

## Available template data:

### User

| Field | Description |
| :--- | :--- |
| .User | The user's username together with discriminator. |
| .User.Username | The user's username. |
| .User.ID | The user's ID. |
| .User.Discriminator | The users's discriminator \(The four digits in a person's username\). |
| .User.Avatar | The user's avatar ID. |
| .User.AvatarURL "256" | Gives the URL for user's avatar, argument "256" is the size of the picture  and can increase/decrease twofold \(e.g. 512, 1024 or 128, 64 etc.\). |
| .User.Bot | Determines whether the target user is a bot - if yes, it will return True. |
| .User.Mention | Mentions user. |
| .RealUsername | Only works with join and leave messages. This can be used to send the real username to a staff channel when invites are censored. |
| .UsernameHasInvite | Only works with join and leave messages. It will determine does the username contain an invite link. |

### Guild / Server

| Field | Description |
| :--- | :--- |
| .Guild.ID | Outputs the ID of the guild. |
| .Guild.Name | Outputs the name of the guild. |
| .Guild.Icon | Outputs the ID of the guild's icon. |
| .Guild.Region | Outputs the region of the guild. |
| .Guild.AfkChannelID | Outputs the AFK channel ID. |
| .Guild.OwnerID | Outputs the ID of the owner. |
| .Guild.JoinedAt | Outputs when the user joined the guild. |
| .Guild.AfkTimeout | Outputs the time when a user gets moved into the AFK channel while not being active. |
| .Guild.MemberCount | Outputs the number of users on a guild. |
| .Guild.VerificationLevel | Outputs the required verification level for the guild. |
| .Guild.EmbedEnabled | Outputs whether embeds are enabled or not, true / false. |

### Member

| Field | Description |
| :--- | :--- |
| .Member.Nick | The nickname for this member. |
| .Member.Roles | A list of role IDs that the member has. |

### Channel

| Field | Description |
| :--- | :--- |
| .Channel.Name | The Name of the channel. |
| .Channel.ID | The ID of the channel. |
| .Channel.Topic | The Topic of the channel. |
| .Channel.NSFW | Outputs whether this channel is NSFW or not. |

### Current User

| Function | Description |
| :--- | :--- |
| currentUserCreated |  The time the current user was created. |
| currentUserAgeHuman |  The account age of the current user in more human readable format  \(`3 days 2 hours`, for example\). |
| currentUserAgeMinutes |  The account age of the current user in minutes. |

### Functions

| Function | Description |
| :--- | :--- |
| `adjective` | Returns a random adjective. |
| `dict key1 value1 key2 value2 etc` | Creates a dictionary \(not many use cases yet\). |
| `sdict "key1" "value1" "key2" "value2"` |  The same as `dict` but with only string keys and can be used in `cembed.` |
| `cslice value1 value2` | Creates a slice \(similar to array\) that can be used elsewhere \(`cembed` and `sdict` for example\). |
| `cembed "list of embed values"` | Function to generate embed inside custom command. [More in-depth here.](../others/custom-embeds.md#embeds-in-custom-commands) |
| `in list value` | Returns true if value is in list. |
| `add x y` | Returns x + y. |
| `seq start stop` | Creates a new array of integer, starting from start and ending at stop. |
| `shuffle list` | Returns a shuffled version of a list. |
| `joinStr seperator str1 str2` | Joins several strings into one, seperated by the first arg the separator, useful for executing commands in templates \(e.g.`{{joinStr "" "1" "2" "3"}} = "123")`. |
| `randInt (stop, or start stop)` | Returns a random integer between 0 and stop, or start - stop if two args are provided. |
| `toString` | Converts something into a string. Usage: `(toString x)`. |
| `toInt` | Converts something into an integer. Usage: `(toInt x)`. |
| `toInt64` | Converts something into an int64. Usage: `(toInt64 x)`. |
| `sendDM "message here"` | Sends the user a direct message, only one DM can be sent per template \(accepts embed objects\). |
| `sendMessage channel_name message` | send `message (string or embed)` in `channel_name`, channel can be either `nil`, the channel ID or the channel's name. |
| `sendMessageNoEscape channel_name message` | send `message (string or embed)` in `channel_name`, channel can be either `nil`, the channel ID or the channel name. Doesn't escape mentions \(e.g. role mentions or @here/@everyone\). |
| `mentionEveryone` | Mentions @everyone. |
| `escapeEveryone "input"` | Escapes everyone mentions in a string. |
| `mentionHere` | Mentions @here |
| `escapeHere "input"` | Escapes here mentions in a string. |
| `escapeEveryoneHere` | Escapes everyone and here mentions in a string. |
| `mentionRoleName "rolename"` | Mentions the first role found with the provided name \(case insensitive\). |
| `mentionRoleID "roleID"` | Mentions the role found with the provided ID. |
| `hasRoleName "rolename"` | Returns true if the user has the role with the specified name \(case insensitive\). |
| `hasRoleID roleid` | Returns true if the user has the role with the specified ID \(use the listroles command for a list of roles\). |
| `addRoleID roleid` |  Add the role with the given ID to the user that triggered the command \(use the listroles command for a list of roles\). |
| `removeRoleID roleid` | Remove the role with the given ID from the user that triggered the command \(use the listroles command for a list of roles\). |
| `giveRoleName target role_name` | Gives a role by name to the target. |
| `giveRoleID target role_ID` | Gives a role by ID to the target. |
| `takeRoleName target role_name` | Take away a role by name from the target. |
| `takeRoleID target role_ID` | Take away a role by ID from the target. |
| `deleteResponse "time"` | Deletes the response after a certain time  \(1-60 seconds\). |
| `deleteTrigger "time"` | Deletes the trigger after a certain time \(1-60 seconds\). |
| `addReactions "👍" "👎"` | Adds each emoji as a reaction to the message that triggered the command \(recognizes unicode emojis and `emojiname:emojiid`\). |
| `addResponseReactions "👍" "👎"` | Adds each emoji as a reaction to the response message \(recognizes unicode emojis and `emojiname:emojiid`\). |
| `exec "command" "args" "args" "args"` | Execute a YAGPDB \(e.g. reverse, roll, kick etc\) in a custom command. Max exec can be run 5 times per command.  |
| `execAdmin "command" "args" "args" "args" etc` | Function the same as exec but will override any permission requirement \(such as the kick permission to use kick command etc.\). |
| `userArg ########` | Function that can be used to retrieve a user from a mention string or ID. |
|  `currentTime` | Gets the current time which can be used in an custom embed. |
| `.CmdArgs` | Get all the arguments passed to the command. |
| `slice "string" integer` | Outputs the "string" after cutting/slicing off integer \(numeric\) value of symbols - e.g. `{{slice "Fox runs" 2}}`outputs `x runs`. For slicing whole words see example below in Snippets. |
| `lower "string"` | Convert the string to lowercase. |
| `title "string"` | Returns string with the first letter of each word capitalized. |

### Branching

| Case | Example |
| :--- | :--- |
| Basic if |  `{{if (condition)}}{{end}}` |
| Not | `{{if not (condition)}}{{end}}` |
| And |  `{{if and (cond1) (cond2) (cond3)}}` |
|  Or |  `{{if or (cond1) (cond2) (cond3)}}` |
| Equals |  `{{if eq .Channel.ID ########}}` |
| Not Equals |  `{{if ne .Channel.ID #######}}` |
| Less than |  `{{if lt (len .Args) 5}}` |
| Greater than |  `{{if gt (len .Args) 1}}` |
| Else if |  `{{if (case statement}} {{else if (case statement}} {{end}}` |
| Else |  `{{if (case statement}} {{else}} output here {{end}}` |

### Snippets

* `<@{{.User.ID}}>` Outputs a mention to the user that called the command.
* `<@###########>` Mentions the user that has the ID \#\#\#\#\#\# \(See [How to get IDs](templates.md#how-to-get-ids) to get ID\).
* `<#&&&&&&&&&&&>` Mentions the channel that has ID &&&&&& \(See [How to get IDs](templates.md#how-to-get-ids) to get ID\).
* `{{if hasRoleName "funrole"}} Has role funrole {{end}}`This will only show if the member has a role with name "funrole" .
* `{{if gt (len .Args) 0}} {{index .Args 1}} {{end}}` Assuming your trigger is a command, will display your first input if input was given.
* `{{if eq .Channel.ID #######}}` Will only show in Channel \#\#\#\#\#.
* `{{if ne .User.ID #######}}` Will ignore if user ID \#\#\#\#\# uses command.
* `{{$d := randInt 10}}` Store the random int into variable $d \(A random number from 0-9\).
* `{{addReactions .CmdArgs}}` Adds the emoji following a trigger as reactions.
* `{{$a := (exec "catfact")}}` Saves the response of the **catfact** command to variable `$a`. 
* `{{$allArgs := (joinStr " " .CmdArgs)}}` Saves all the argument to a variable `$allArgs`. 
* `{{$args:= (joinStr " " (slice .CmdArgs 1))}}`  Saves all the arguments except the first one to a variable `$args`. 
* `{{/* this is a comment */}}`For commenting something inside a template, use this syntax.

## How to get IDs <a id="how-to-get-ids"></a>

**User IDs:** Can be found by mentioning the user then adding a \ such as `\@jonas747#0001` . Alternatively if you have developer mode on, you can right click and select Copy ID

**Channel IDs** Can be found by mentioning the channel then adding a \ such as `\#announcements`. Alternatively if you have developer mode on, you can right click on the channel and select Copy ID

**Role IDs**: Use the `listroles`command.

**Emote IDs:** 

If it is a **custom emote**, adding a \ in front of the emote such as `\:yagpdg:` will display the name along along with the ID such as  `<:yag:277569741932068864>`.

If it is a **animated emote**, do the same steps as a normal emote. If you do not have Discord Nitro, you can have a friend or a bot use the emote and right click on the emote to open its link. The ID will be a part of the URL.

If it is a **default emote**, look up the Unicode for the emote on Google. Note that some of the more customized default emotes such as some of the the family emotes will not work in any of the YAGPDB commands. 

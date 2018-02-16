
## Extended Ban Mod API

### ban_player

`xban.ban_player(player_or_ip, source, expires, reason)`

Ban a player and all of his/her alternative names and IPs.

#### Arguments:

* `player_or_ip` - Player to search for and ban. See note 1 below.
* `source` - Source of the ban. See note 2 below.
* `expires` - Time at which the ban expires. If nil, ban is permanent.
* `reason` - Reason for ban.

### unban_player

`xban.unban_player(player_or_ip, source, reason)`

Unban a player and all of his/her alternative names and IPs.  A reason
may be given for this unbanning, so other moderators can follow your
thoughts.


#### Arguments:

* `player_or_ip` - Player to search for and unban.
* `source` - Source of the ban. See note 2 below.
* `reason` - Reason for unbanning.

### add_record:

`xban.add_record(player, record)`

Adds a record to the player's criminal record.

#### Arguments:

* `player` - Name of a player
* `record` - a xban record (see below)

### Player record format:


	local record = {
      source = "admin",
      time = os.time(),
      expires = nil,
      reason = "bad behaviour",
      type = "ban",
	}

* `source` - who issued the record
* `time` - time at which the record was issued
* `expires` - time at which the record expires, `nil` for never
* `reason` - reason for record
* `type` - type of record.


### Notes

* 1: If player is currently online, all his accounts are kicked.
* 2: Mods using the xban API are advised to use the `"modname:source"`
format for `source` (for example: `"anticheat:main"`).

# moobot-obs

# Announcement: this should be stable by now - I will write an update after a successful stream

## Requirements:
- Docker - Linux Containers

- Docker-Compose

- Streaming Setup from https://github.com/moo-the-cow/streaming MINUS the noalbs version, which this bot will replace. I will properly add this here in time


## Setup (based on windows environment):

modify your [appsettings.conf](appsettings.conf)

fill out everything that is marked like this `<REPLACE ME>`

put all the files into a folder

in a Terminal type:
```
docker compose up -d
```

## Features
option to send requests from twitch to obs and returning data (via whisper or normal chat message in public)

automatic scene switching on low bitrate/high rtt

persmissions on each command

## Main Command
| Object (do not modify!) | Name (alias) | Enabled | Role Permission |
| ---- | ---- | :---: | -------- |
| Obs | !obs | true |  broadcaster, moderator  |

## Sub Commands

| Object (do not modify!) | Name (alias) | Enabled | Whisper result | Role Permission |
| ---- | ---- | :---: | --- | -------- |
| GetVersion | GetVersion | true | false |  broadcaster, moderator  |
| GetStats | GetStats | true | true | broadcaster, moderator  |
| SetCurrentSceneCollection | SetCurrentSceneCollection | true | null | broadcaster, moderator |
| SetCurrentProgramScene | SetCurrentProgramScene | true | null | broadcaster, moderator |
| StartStream | start | true | null | broadcaster, moderator |
| StopStream | stop | true | null | broadcaster, moderator |
| StartRecord | SetSceneItemEnabled | true | null | broadcaster, moderator |
| StopRecord | SetSceneItemEnabled | true | null | broadcaster, moderator |
| SetRtt | SetSceneItemEnabled | true | null | broadcaster, moderator |
| SetBitrate | SetSceneItemEnabled | true | null | broadcaster, moderator |
| Autoswitch | SetSceneItemEnabled | true | null | broadcaster, moderator |
| SendTwitchMessages | SetSceneItemEnabled | true | null | broadcaster, moderator |

### Group Roles
(attribute `group`)

broadcaster, moderator, vip, subscriber, turbo, partner, staff, everyone

### User Role
Requires the attribute `username` and then the username value `<USERNAME>`

example (non-working) entry for a user
```
"DummyCommand": {"name":"DummyCommandName", "enabled":true, "permission":[{"group":"moderator","cooldown":0},{"username":"m_o_o_","cooldown":0}]},
```

## Usage on Twitch
`!obs GetVersion` will show

*MoobsWebsocket v1.0 on Moobot-Obs (OBS: <OBS_VERSION>)*

`!obs GetStats` will whisper the user who triggerd the command OBS Stats (only remaining recording diskspace for now)

*Diskspace Left: 94,26 GB*

`!obs SetCurrentSceneCollection <SCENECOLLECTION_NAME>` will switch to the scene collection with that name

`!obs SetCurrentProgramScene <SCENE_NAME>` will switch to the scene with that name

`!obs SetSceneItemEnabled <ITEM_NAME>` will switch to the Source of the current selected Scene with that name

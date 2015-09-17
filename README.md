# Secure Scuttlebutt

 - [Learn About SSB](./learn.md)
 - Articles
   - [Design Challenge: Avoiding Centralization and Singletons](./articles/design-challenge-avoid-centralization-and-singletons.md)
   - [Design Challenge: Sybil Attacks](./articles/design-challenge-sybil-attack.md)
   - [Desirable Properties for a Secure Channel](./articles/desirable-properties-for-a-secure-channel.md)
   - [Secure, Private Channels: the Good, the Bad, and the Ugly](./articles/secure-private-channels.md)
 - Scuttlebot
   - [Repo & Overview](https://github.com/ssbc/scuttlebot)
   - [API Docs](https://github.com/ssbc/scuttlebot/blob/master/api.md)
   - Plugins
     - [Blobs](https://github.com/ssbc/scuttlebot/blob/master/plugins/blobs.md)
     - [Block](https://github.com/ssbc/scuttlebot/blob/master/plugins/block.md)
     - [Friends](https://github.com/ssbc/scuttlebot/blob/master/plugins/friends.md)
     - [Gossip](https://github.com/ssbc/scuttlebot/blob/master/plugins/gossip.md)
     - [Invite](https://github.com/ssbc/scuttlebot/blob/master/plugins/invite.md)
     - [Private](https://github.com/ssbc/scuttlebot/blob/master/plugins/private.md)
     - [Replicate](https://github.com/ssbc/scuttlebot/blob/master/plugins/replicate.md)
 - Pull-streams
   - [Repo & Overview](https://github.com/dominictarr/pull-stream)
   - [Pull Sources](https://github.com/dominictarr/pull-stream/blob/master/docs/sources.md)
   - [Pull Throughs](https://github.com/dominictarr/pull-stream/blob/master/docs/throughs.md)
   - [Pull Sinks](https://github.com/dominictarr/pull-stream/blob/master/docs/sinks.md)


## Glossary

 - [Secure-Scuttlebutt](https://github.com/ssbc/secure-scuttlebutt) (SSB) - A protocol for replicating logs in a decentralized mesh. The SSB library wraps leveldb with tools for reading, writing to, and replicating feeds.
 - [Scuttlebot](https://github.com/ssbc/scuttlebot) - A secure-scuttlebutt server and client. Includes the database, networking, blob exchange protocol, and command-line tools.
 - Pub Servers - SSB peers which run on publicly IPs, and provide connectivity and hosting for users on private IPs. Pubs are not privileged, and do not hold special authority in the network. They are not hosts.
 - Invite codes - Tokens which may be used to command specific Pub servers to follow a user. These are used to join Pubs.
 - Feeds - a user's stream of JSON data. Also called logs.
 - Gossip - a networking technique where peers connect randomly to each other and ask for new updates. Gossip is unique for not relying on any central server to push information. Instead, the information travels peer-to-peer.


## Overview

Scuttlebot is a mesh database for JSON logs.
It uses a trustless protocol, so any device can participate in the mesh.
It's used with desktop applications to publish and syncronize user-data.


### Install prerequisites

Current install steps are:

```
# ubuntu
apt-get install automake
# osx
brew install automake
```

Also, you'll need to use iojs@2.
The easiest way to get this is nvm.

```
nvm install iojs-v2.5.0
```


### Install scuttlebot

To begin, install the prerequisites as above.

```
npm install -g scuttlebot
```

Start scuttlebot as server.

```
sbot server
```

Then, in another session, use the cli tool to access the API:

```
sbot whoami
sbot publish --type post --text "Hello, world"
sbot log
```

You can get help with `-h`.

If you're running a pub server, you'll want to create invites:

```
# create an invite code that may be used 1 time.
sbot invite.create 1
```

This may now be given out to friends!

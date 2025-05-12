# General Requirements

* [Download](https://nodejs.org/en/download) Node.js Version 18+ For the bot.
* [Download](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) Java JRE Version 17+ For Lavalink.

#### Lavalink & Plugins <a href="#lavalink--plugins" id="lavalink--plugins"></a>

* [Download](https://github.com/lavalink-devs/Lavalink/releases) Lavalink Server 4.0.4+
  * lavalink-plugin
  * lavasearch
  * lavasrc
  *   youtube-plugin

      **For easier setup, clone this repo** [**https://github.com/krushna06/Lavalink-Server**](https://github.com/krushna06/Lavalink-Server)

### API Keys <a href="#api-keys" id="api-keys"></a>

It is recommended to have the following API keys to optimize Wace's features and use at its maximum potential.

```yaml
lavasrc:
  applemusic:
    keyID: your Apple Developer Key ID
    teamID: your Apple Developer Team ID
    musicKitKey: |
      -----BEGIN PRIVATE KEY-----
      your Apple Music private key
      -----END PRIVATE KEY-----
    mediaAPIToken: ""  # optional if generated dynamically

  deezer:
    masterDecryptionKey: your Deezer master decryption key

  spotify:
    clientId: your Spotify client ID
    clientSecret: your Spotify client secret
    spDc: your Spotify sp_dc cookie

  yandexmusic:
    accessToken: your Yandex Music access token

jiosaavn:
  apiURL: https://saavn.dev/api  # already provided, no key needed

youtube:
  oauth:
    enabled: true
    refreshToken: your YouTube refresh token
```

# REST API

If the **field** title have `?`, that means data can nullable

## Track API

| Field      | Type                            | Description                |
| ---------- | ------------------------------- | -------------------------- |
| title      | string                          | The title of track         |
| uri        | string                          | The URL of track           |
| length     | number                          | The duration of track      |
| thumbnail? | string                          | The artwork URL of track   |
| author?    | string                          | The author URL of track    |
| requester? | [User](broken-reference) object | The requester URL of track |

## User API

| Field             | Type   | Description                     |
| ----------------- | ------ | ------------------------------- |
| id                | string | The discord id of user          |
| username          | string | The discord username of user    |
| globalName        | string | The discord global name of user |
| defaultAvatarURL? | string | The discord avatar url of user  |

## Skip mode API

* `previous`: Appears when the track is end by using previous
* `normal`: Appears when the track is end normally

## Skip mode API (REST)

* `previous`: Play the previous track
* `skip`: Play the next track

## Loop mode API

* `queue`: Loop the current queue
* `song`: Loop the current track
* `none`: Disable loop

## Commands API

| Field        | Type   | Description                    |
| ------------ | ------ | ------------------------------ |
| name         | string | The name of command            |
| description  | string | The description of command     |
| category     | string | The category of command        |
| accessableby | string | Command can accessable by who? |
| usage        | string | The usage of command           |
| aliases      | string | The aliases of command         |

## Member API

* `true`: User is in the voice
* `false`: User not in the voice
* `notGiven`: Not given the user id

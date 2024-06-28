# Websocket

## Introduction

Wace provides an event system that track player activity of the bot through websocket. This is for the development of the dashboard with an easy way for middle developer.

This doc will explain, providing example clearly for each event

**Note:** If the **field** title have `?`, that means data can nullable

## Connect

You can establish a WebSocket connection against the path `/v1/websocket`

When opening a websocket connection, you must supply 2 required headers:

| Header Name   | Description                                       |
| ------------- | ------------------------------------------------- |
| authorization | The password you set in your app.yml config       |
| guild-id      | The guild id which you want bot to open websocket |

**Note:** If you use the guild id which doesn't exist on wace to connect websocket, it won't send any events.

## Op (event)

#### playerCreate

Dispatched when a player is created.

| Field | Type   | Description                    |
| ----- | ------ | ------------------------------ |
| op    | string | The event name                 |
| guild | string | The guild that have this event |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "playerCreate",
  "guild": "1228698769655332884",
}
```

</details>

#### playerDestroy

Dispatched when a player is destroyed.

| Field | Type   | Description                    |
| ----- | ------ | ------------------------------ |
| op    | string | The event name                 |
| guild | string | The guild that have this event |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "playerDestroy",
  "guild": "1228698769655332884",
}
```

</details>

#### playerPause

Dispatched when a player is paused.

| Field | Type   | Description                    |
| ----- | ------ | ------------------------------ |
| op    | string | The event name                 |
| guild | string | The guild that have this event |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "playerPause",
  "guild": "1228698769655332884",
}
```

</details>

#### playerResume

Dispatched when a player is resume.

| Field | Type   | Description                    |
| ----- | ------ | ------------------------------ |
| op    | string | The event name                 |
| guild | string | The guild that have this event |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "playerResume",
  "guild": "1228698769655332884",
}
```

</details>

#### playerUpdate

Dispatched when a player is update.

| Field    | Type   | Description                        |
| -------- | ------ | ---------------------------------- |
| op       | string | The event name                     |
| guild    | string | The guild that have this event     |
| position | number | The current position of this track |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "playerUpdate",
  "guild": "1228698769655332884",
  "position": 5880,
}
```

</details>

#### trackStart

Dispatched when a track in player is started.

| Field | Type         | Description                         |
| ----- | ------------ | ----------------------------------- |
| op    | string       | The event name                      |
| guild | string       | The guild that have this event      |
| data? | Track object | The track info of now playing track |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "trackStart",
  "guild": "1228698769655332884",
  "data": {
    "title": "2Pac - Dear Mama",
    "uri": "https://www.youtube.com/watch?v=Mb1ZvUDvLDY",
    "length": 276000,
    "thumbnail": "https://i.ytimg.com/vi/Mb1ZvUDvLDY/maxresdefault.jpg",
    "author": "2PacVEVO",
    "requester": {
      "id": "853620650592567304",
      "username": "n0step_",
      "globalName": "n0step_",
      "defaultAvatarURL": "https://images-ext-1.discordapp.net/external/MGI1XKlpRX1rhYHVULul9k0inXehUC_DrBe2drNURaI/%3Fsize%3D2048/https/cdn.discordapp.com/avatars/853620650592567304/1fa5daa2aaa94a01b3a656d178122e3c.webp?format=webp&width=280&height=280",
    }
  }
}
```

</details>

#### trackEnd

Dispatched when a track in player is ended.

| Field | Type         | Description                      |
| ----- | ------------ | -------------------------------- |
| op    | string       | The event name                   |
| guild | string       | The guild that have this event   |
| data? | Track object | The track info of previous track |
| mode  | Mode string  | The end mode of this event       |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "trackEnd",
  "guild": "1228698769655332884",
  "data": {
    "title": "2Pac - Dear Mama",
    "uri": "https://www.youtube.com/watch?v=Mb1ZvUDvLDY",
    "length": 276000,
    "thumbnail": "https://i.ytimg.com/vi/Mb1ZvUDvLDY/maxresdefault.jpg",
    "author": "2PacVEVO",
    "requester": {
      "id": "853620650592567304",
      "username": "n0step_",
      "globalName": "n0step_",
      "defaultAvatarURL": "https://images-ext-1.discordapp.net/external/MGI1XKlpRX1rhYHVULul9k0inXehUC_DrBe2drNURaI/%3Fsize%3D2048/https/cdn.discordapp.com/avatars/853620650592567304/1fa5daa2aaa94a01b3a656d178122e3c.webp?format=webp&width=280&height=280",
    }
  }
}
```

</details>

#### memberJoin

Dispatched when a memeber is joined.

| Field  | Type   | Description                                   |
| ------ | ------ | --------------------------------------------- |
| op     | string | The event name                                |
| guild  | string | The guild that have this event                |
| userId | string | The discord id of memeber that join the voice |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "memberJoin",
  "guild": "1228698769655332884",
  "userId": "853620650592567304",
}
```

</details>

#### memberLeave

Dispatched when a memeber is leaved.

| Field  | Type   | Description                                    |
| ------ | ------ | ---------------------------------------------- |
| op     | string | The event name                                 |
| guild  | string | The guild that have this event                 |
| userId | string | The discord id of memeber that leave the voice |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "memberLeave",
  "guild": "1228698769655332884",
  "userId": "853620650592567304",
}
```

</details>

#### playerVolume

Dispatched when a player volume is changed.

| Field  | Type   | Description                    |
| ------ | ------ | ------------------------------ |
| op     | string | The event name                 |
| guild  | string | The guild that have this event |
| volume | number | The changed player volume      |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "playerVolume",
  "guild": "1228698769655332884",
  "volume": 90,
}
```

</details>

#### playerLoop

Dispatched when a player volume is changed.

| Field | Type        | Description                    |
| ----- | ----------- | ------------------------------ |
| op    | string      | The event name                 |
| guild | string      | The guild that have this event |
| mode  | Mode string | The changed player loop mode   |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "playerLoop",
  "guild": "1228698769655332884",
  "mode": "queue",
}
```

</details>

#### playerClearQueue

Dispatched when a player queue is cleared.

| Field | Type   | Description                    |
| ----- | ------ | ------------------------------ |
| op    | string | The event name                 |
| guild | string | The guild that have this event |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "playerClearQueue",
  "guild": "1228698769655332884",
}
```

</details>

#### playerQueueRemove

Dispatched when a player track from queue is removed.

| Field | Type         | Description                          |
| ----- | ------------ | ------------------------------------ |
| op    | string       | The event name                       |
| guild | string       | The guild that have this event       |
| data  | Track object | The track info                       |
| index | number       | The index for removed track in array |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "playerQueueRemove",
  "guild": "1228698769655332884",
  "data": {
    "title": "2Pac - Dear Mama",
    "uri": "https://www.youtube.com/watch?v=Mb1ZvUDvLDY",
    "length": 276000,
    "thumbnail": "https://i.ytimg.com/vi/Mb1ZvUDvLDY/maxresdefault.jpg",
    "author": "2PacVEVO",
    "requester": {
      "id": "853620650592567304",
      "username": "n0step_",
      "globalName": "n0step_",
      "defaultAvatarURL": "https://images-ext-1.discordapp.net/external/MGI1XKlpRX1rhYHVULul9k0inXehUC_DrBe2drNURaI/%3Fsize%3D2048/https/cdn.discordapp.com/avatars/853620650592567304/1fa5daa2aaa94a01b3a656d178122e3c.webp?format=webp&width=280&height=280",
    }
  },
  "index": 4
}
```

</details>

#### playerQueueInsert

Dispatched when a player track from queue is inserted.

| Field | Type         | Description                           |
| ----- | ------------ | ------------------------------------- |
| op    | string       | The event name                        |
| guild | string       | The guild that have this event        |
| data  | Track object | The track info                        |
| index | number       | The index for inserted track in array |

<details>

<summary>Example Payload</summary>

```json
{
  "op": "playerQueueInsert",
  "guild": "1228698769655332884",
  "data": {
    "title": "2Pac - Dear Mama",
    "uri": "https://www.youtube.com/watch?v=Mb1ZvUDvLDY",
    "length": 276000,
    "thumbnail": "https://i.ytimg.com/vi/Mb1ZvUDvLDY/maxresdefault.jpg",
    "author": "2PacVEVO",
    "requester": {
      "id": "853620650592567304",
      "username": "n0step_",
      "globalName": "n0step_",
      "defaultAvatarURL": "https://images-ext-1.discordapp.net/external/MGI1XKlpRX1rhYHVULul9k0inXehUC_DrBe2drNURaI/%3Fsize%3D2048/https/cdn.discordapp.com/avatars/853620650592567304/1fa5daa2aaa94a01b3a656d178122e3c.webp?format=webp&width=280&height=280",
    }
  },
  "index": 4
}
```

</details>

#### playerQueueShuffle

Dispatched when a player track from queue is inserted.

| Field           | Type        | Description                         |
| --------------- | ----------- | ----------------------------------- |
| op              | string      | The event name                      |
| guild           | string      | The guild that have this event      |
| queue           | Track array | The track queue info that shuffered |
|                 |             |                                     |
| Example Payload |             |                                     |

```json
{
  "op": "playerQueueShuffle",
  "guild": "1228698769655332884",
  "queue": [
    {
      "title": "2Pac - Dear Mama",
      "uri": "https://www.youtube.com/watch?v=Mb1ZvUDvLDY",
      "length": 276000,
      "thumbnail": "https://i.ytimg.com/vi/Mb1ZvUDvLDY/maxresdefault.jpg",
      "author": "2PacVEVO",
      "requester": {
        "id": "853620650592567304",
        "username": "n0step_",
        "globalName": "n0step_",
        "defaultAvatarURL": "https://images-ext-1.discordapp.net/external/MGI1XKlpRX1rhYHVULul9k0inXehUC_DrBe2drNURaI/%3Fsize%3D2048/https/cdn.discordapp.com/avatars/853620650592567304/1fa5daa2aaa94a01b3a656d178122e3c.webp?format=webp&width=280&height=280",
      }
    }
  ],
}
```

#### playerQueueSkip

Dispatched when a player skip to another index of queue.

| Field           | Type        | Description                         |
| --------------- | ----------- | ----------------------------------- |
| op              | string      | The event name                      |
| guild           | string      | The guild that have this event      |
| queue           | Track array | The track queue info that shuffered |
|                 |             |                                     |
| Example Payload |             |                                     |

```json
{
  "op": "playerQueueSkip",
  "guild": "1228698769655332884",
  "queue": [
    {
      "title": "2Pac - Dear Mama",
      "uri": "https://www.youtube.com/watch?v=Mb1ZvUDvLDY",
      "length": 276000,
      "thumbnail": "https://i.ytimg.com/vi/Mb1ZvUDvLDY/maxresdefault.jpg",
      "author": "2PacVEVO",
      "requester": {
        "id": "853620650592567304",
        "username": "n0step_",
        "globalName": "n0step_",
        "defaultAvatarURL": "https://images-ext-1.discordapp.net/external/MGI1XKlpRX1rhYHVULul9k0inXehUC_DrBe2drNURaI/%3Fsize%3D2048/https/cdn.discordapp.com/avatars/853620650592567304/1fa5daa2aaa94a01b3a656d178122e3c.webp?format=webp&width=280&height=280",
      }
    }
  ],
}
```

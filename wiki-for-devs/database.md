# Database

## Introduction

Wace provides a rest system to control the bot through http. This is for developing dashboard with an easy way for middle developer.

This doc will explain, providing example clearly for each endpoints

## Note

* Most routes require the `authorization` header with the configured password.
* Example header: `authorization: youshallnotpass`
* If the **field** title have `?`, that means data can nullable
* If the endpoints have `[no-auth]` in the title, that means it can access without `authorization` header

## Endpoints

#### \[no-auth] GET /catgirls

This endpoints is for health check

**Response:**

| Field | Type   | Description       |
| ----- | ------ | ----------------- |
| Wace  | string | The random string |

**Example response:**

```json
{
  "wace": "💀"
}
```

#### GET /v1/commands

This endpoints is for get all command that avaliable on this bot

**Response:**

| Field | Type          | Description       |
| ----- | ------------- | ----------------- |
| data  | Command array | The command array |

**Example response:**

```json
{
  "data": [
    {
      "name": "avatar",
      "description": "Show your or someone else's profile picture",
      "category": "Image",
      "accessableby": "Member",
      "usage": "<mention>",
      "aliases": []
    },
  ]
}
```

#### GET /v1/players/{guildId}

This endpoints is for get current player from given guild (remove {} before requesting)

**Params**

* guildId: The discord guild id have player

**Response:**

| Field    | Type         | Description                                            |
| -------- | ------------ | ------------------------------------------------------ |
| guildId  | string       | The discord guild id have player                       |
| loop     | Mode string  | The current loop mode                                  |
| member   | isIn string  | The status of current member (if user in voice or not) |
| position | number       | The current position                                   |
| current  | Track object | The current track info                                 |
| queue    | Track array  | The current track queue                                |

**Example response:**

```json
{
  "guildId": "1228698769655332884",
  "loop": "none",
  "pause": false,
  "member": "true",
  "position": 90120,
  "current": {
    "title": "Bruno Mars - That’s What I Like [Official Music Video]",
    "uri": "https://www.youtube.com/watch?v=PMivT7MJ41M",
    "length": 211000,
    "thumbnail": "https://i.ytimg.com/vi/PMivT7MJ41M/mqdefault.jpg",
    "author": "Bruno Mars",
    "requester": {
      "id": "853620650592567304",
      "username": "n0step_",
      "globalName": "n0step_",
      "defaultAvatarURL": "https://images-ext-1.discordapp.net/external/MGI1XKlpRX1rhYHVULul9k0inXehUC_DrBe2drNURaI/%3Fsize%3D2048/https/cdn.discordapp.com/avatars/853620650592567304/1fa5daa2aaa94a01b3a656d178122e3c.webp?format=webp&width=280&height=280"
    }
  },
  "queue": []
}
```

#### GET /v1/players/{guildId}/loop

This endpoints is for get current player loop state from given guild (remove {} before requesting)

**Params**

* guildId: The discord guild id have player

**Response:**

| Field | Type        | Description           |
| ----- | ----------- | --------------------- |
| data  | Mode string | The current loop mode |

**Example response:**

```json
{
  "data": "none"
}
```

#### GET /v1/players/{guildId}/pause

This endpoints is for get current player pause state from given guild (remove {} before requesting)

**Params**

* guildId: The discord guild id have player

**Response:**

| Field | Type    | Description            |
| ----- | ------- | ---------------------- |
| data  | boolean | The current pause mode |

**Example response:**

```json
{
  "data": false
}
```

#### GET /v1/players/{guildId}/pause

This endpoints is for get current player pause state from given guild (remove {} before requesting)

**Params**

* guildId: The discord guild id have player

**Response:**

| Field | Type    | Description            |
| ----- | ------- | ---------------------- |
| data  | boolean | The current pause mode |

**Example response:**

```json
{
  "data": false
}
```

#### GET /v1/players/{guildId}/position

This endpoints is for get current player position state from given guild (remove {} before requesting)

**Params**

* guildId: The discord guild id have player

**Response:**

| Field | Type   | Description          |
| ----- | ------ | -------------------- |
| data  | number | The current position |

**Example response:**

```json
{
  "data": 5880
}
```

#### GET /v1/players/{guildId}/current

This endpoints is for get current track from given guild (remove {} before requesting)

**Params**

* guildId: The discord guild id have player

**Response:**

| Field | Type         | Description            |
| ----- | ------------ | ---------------------- |
| data  | Track object | The current track data |

**Example response:**

```json
{
  "data": {
    "title": "Bruno Mars - That’s What I Like [Official Music Video]",
    "uri": "https://www.youtube.com/watch?v=PMivT7MJ41M",
    "length": 211000,
    "thumbnail": "https://i.ytimg.com/vi/PMivT7MJ41M/mqdefault.jpg",
    "author": "Bruno Mars",
    "requester": {
      "id": "853620650592567304",
      "username": "n0step_",
      "globalName": "n0step_",
      "defaultAvatarURL": "https://images-ext-1.discordapp.net/external/MGI1XKlpRX1rhYHVULul9k0inXehUC_DrBe2drNURaI/%3Fsize%3D2048/https/cdn.discordapp.com/avatars/853620650592567304/1fa5daa2aaa94a01b3a656d178122e3c.webp?format=webp&width=280&height=280"
    }
  }
}
```

#### GET /v1/players/{guildId}/queue

This endpoints is for get current queue from given guild (remove {} before requesting)

**Params**

* guildId: The discord guild id have player

**Response:**

| Field | Type        | Description            |
| ----- | ----------- | ---------------------- |
| data  | Track array | The current queue data |

**Example response:**

```json
{
  "data": [
    {
      "title": "Bruno Mars - That’s What I Like [Official Music Video]",
      "uri": "https://www.youtube.com/watch?v=PMivT7MJ41M",
      "length": 211000,
      "thumbnail": "https://i.ytimg.com/vi/PMivT7MJ41M/mqdefault.jpg",
      "author": "Bruno Mars",
      "requester": {
        "id": "853620650592567304",
        "username": "n0step_",
        "globalName": "n0step_",
        "defaultAvatarURL": "https://images-ext-1.discordapp.net/external/MGI1XKlpRX1rhYHVULul9k0inXehUC_DrBe2drNURaI/%3Fsize%3D2048/https/cdn.discordapp.com/avatars/853620650592567304/1fa5daa2aaa94a01b3a656d178122e3c.webp?format=webp&width=280&height=280"
      }
    }
  ]
}
```

#### GET /v1/players/{guildId}/member/{userId}

This endpoints is for get current queue from given guild (remove {} before requesting)

**Params**

* guildId: The discord guild id have player
* userId: The discord user id

**Response:**

| Field | Type    | Description                                    |
| ----- | ------- | ---------------------------------------------- |
| data  | boolean | The user voice state (if user in voice or not) |

**Example response:**

```json
{
  "data": true
}
```

#### DELETE /v1/players/{guildId}

This endpoints with DELETE method will destroy the current player with given guild (remove {} before requesting)

**Params**

* guildId: The discord guild id have player

**Response:** No context: 204

#### POST /v1/players

This endpoints with POST method will create player with given guild

**Body**

| Field   | Type   | Description                |
| ------- | ------ | -------------------------- |
| guildId | string | The given discord guild id |
| userId  | string | The given discord user id  |

**Response:**

| Field   | Type    | Description                                 |
| ------- | ------- | ------------------------------------------- |
| guildId | string  | The created player discord guild id         |
| voiceId | string  | The created player discord voice channel id |
| shardId | number  | The created player discord shard id         |
| textId  | string  | The created player discord text channel id  |
| volume  | number  | The created player volume                   |
| deaf    | boolean | The created player deaf state (always true) |

**Example response:**

```json
{
  "guildId": "1228698769655332884",
  "voiceId": 1216669628374450186,
  "textId": "",
  "shardId": 0,
  "deaf": true,
  "volume": 100,
}
```

#### PATCH /v1/players/{guildId}

This endpoints with PATCH method will modify the player with given guild (remove {} before requesting)

**Params**

* guildId: The discord guild id have player

**Body**

| Field     | Type        | Description                             |
| --------- | ----------- | --------------------------------------- |
| loop?     | Mode string | The given loop mode                     |
| skipMode? | Mode string | The given skip mode                     |
| position? | number      | The given given track position          |
| volume?   | number      | The given volume (0 to 1000)            |
| add?      | Array       | The given track url array (Must be URL) |

**Response:**

| Field    | Type        | Description                     |
| -------- | ----------- | ------------------------------- |
| loop     | Mode string | The patched loop mode           |
| skiped   | boolean     | If the skip mode is choosen     |
| previous | boolean     | If the previous mode is choosen |
| position | number      | The patched position            |
| volume   | number      | The patched volume              |
| add      | Track array | The patched track array         |

**Example response:**

```json
{
  "loop": "queue",
  "skiped": false,
  "previous": false,
  "position": 0,
  "volume": 70,
  "added": [
    {
      "title": "タイニーリトル・アジアンタム",
      "uri": "https://www.youtube.com/watch?v=rB7XFQgJHBI",
      "length": 351000,
      "thumbnail": "https://i.ytimg.com/vi/rB7XFQgJHBI/maxresdefault.jpg?sqp=-oaymwEmCIAKENAF8quKqQMa8AEB-AH-CYAC0AWKAgwIABABGD0gZSghMA8=&rs=AOn4CLAygSsC50atX7sQ9qI6iIpXRToR1A",
      "author": "Shibayan Records",
      "requester": null
    }
  ]
}
```

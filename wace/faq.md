# FAQ

### 1.Why do I have `Invalid config [MissingKey]` error log?

MongoDB

```yml
features:
  DATABASE:
    driver: "mongodb"
    config: 
      uri: "mongodb://127.0.0.1:27017/wacedb"
```

MySQL

```yml
features:
  DATABASE:
    driver: "mysql"
    config: 
      host: "localhost"
      user: "me"
      password: "secret"
      database: "my_db"
```

JSON

```yml
features:
  DATABASE:
    driver: "json"
    config: 
      path: "./wace.database.json"
```

PostgresSQL

```yml
features:
  DATABASE:
    driver: "postgres"
    config: 
      host: "localhost"
      user: "me"
      password: "secret"
      database: "my_db"
```

### 2: Why I have `Error: Used disallowed intents` error log?

Because you have message\_content enabled on your bot, you have 2 ways to fix this:

1: Disable message\_content on the bot:

```yml
features:
  MESSAGE_CONTENT:
    enable: false
    commands: 
      enable: false
      prefix: "w!" # The prefix you want
```

2: Enable message\_content on discord developer portal.

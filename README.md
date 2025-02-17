# MSM-Server-Tools
Tools for interacting with the MSM (My Singing Monsters) Servers made with ease of use in mind.

## Links:
[Settings](#settings)
[Authorization](#authorization)

Settings
------
In MSM Server Tools there are multiple settings you can customize, for example, if you want to connect to your own custom server, set the custom server ip to `127.0.0.1` (localhost) or your own server ip, default: `null`.
Or, you can set your port to what your server supports, default: `9933`.

You can find a full list of settings **[here](https://example.com).**

Authorization
------
In My Singing Monsters, before anything happens, the client sends a request to **https://auth.bbbgame.net/auth/api/token/** which in turn gives you your User Game ID (user_game_id) and most importantly, your *authorization token* (token). 

In MSM Server Tools you will click Authorization before you can do anything else and it'll create a new account by sending a request to **https//auth.bbbgame.net/auth/api/anon_account** which creates a new *anonymous* account, and responds with a Username, Password, Account ID, User Game ID & Authorization Token. I'm not sure why theres 3 things for account identification.

One of the params MSM sends to the URL is G (Game ID), Mobile MSM Servers are `1`, and PC MSM Servers are `27`,
another is T (Login Type), Email = `email`, Anonymous = `anon` & Game Center = `gc`.

Oddly enough, it doesn't check how many accounts you've created on that IP if you aren't on the mobile servers. But if you are using the mobile servers, it does check.

[License](https://github.com/riotschoolacc/MSM-Server-Tools/LICENSE)
[Security](https://github.com/riotschoolacc/MSM-Server-Tools/SECURITY.md)

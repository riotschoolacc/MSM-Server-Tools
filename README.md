# MSM-Server-Tools
Tools for interacting with the MSM (My Singing Monsters) Servers made with ease of use in mind.

## Links:
[Settings](#settings)
[Authorization](#authorization)
[Login](#login)

[License](https://github.com/riotschoolacc/MSM-Server-Tools/LICENSE)
[Security](https://github.com/riotschoolacc/MSM-Server-Tools/SECURITY.md)

> [!CAUTION]
> Creating too many accounts in a small time period (around 1000, from experience) **will** get you IP Banned from the My Singing Monsters servers for a couple of minutes.\n
> But don't worry, you will be unbanned after around (from experience) 7 minutes.

Settings
------
In MSM Server Tools there are multiple settings you can customize, for example, if you want to connect to your own custom server, set the custom server ip to `127.0.0.1` (localhost) or your own server ip, default: `null`.
Or, you can set your port to what your server supports, default: `9933`.

You can find a full list of settings **[here](https://example.com).**

> [!TIP]
> You should keep all the *Main* Settings the same to avoid problems.

Authorization
------
In My Singing Monsters, before anything happens, the client sends a request to **https://auth.bbbgame.net/auth/api/token/** which in turn gives you your User Game ID (`user_game_id`) and most importantly, your *authorization token* (`token`). 

In MSM Server Tools you will click Authorization before you can do anything else and it'll create a new account by sending a request to **https//auth.bbbgame.net/auth/api/anon_account** which creates a new *anonymous* account, and responds with a Username, Password, Account ID, User Game ID & Authorization Token. I'm not sure why theres 3 things for account identification.

One of the params MSM sends to the URL is G (Game ID), Mobile MSM Servers are `1`, and PC MSM Servers are `27`,
another is T (Login Type), Email = `email`, Anonymous = `anon` & Game Center = `gc`.

> [!WARNING]
> You will need to re-authenticate every 10 minutes due to there being a Expiration Time inside the Token.

Oddly enough, it doesn't check how many accounts you've created on that IP if you aren't on the mobile servers. But if you are using the mobile servers, it does check, and refuses to allow you to create more if you have multiple.

Pregame Setup
------
After Authentication, the client sends a request to **https://msmpc.bbbgame.net/pregame_setup.php** with one param being the returned Auth Token from earlier. (mobile: **https://msm-auth.bbbgame.net/pregame_setup.php**)
Which in turn gives you a Server IP (`server_ip`) and Update Files Url (`content_url`).

Login
------
Once the Server IP is located, you should in MSM Server Tools click *Server Login* which uses a wonderful [Smartfox2x implementation](https://github.com/MSM-Hacks/pyfox2x) made by **[MSM Hacks](https://github.com/MSM-Hacks)**.
[English Documentation](https://github.com/mlnitoon2/pyfox2x)
To connect to the Server using the responded IP or [Custom Server IP](#settings) and port `9933` (Default Smartfox2x port and the one MSMs Servers Use) or the [Custom Server Port](#settings). If its successful, MSM Server Tools will send a Login Request to the server,

with params:
Zone: `My Singing Monsters` or your [Custom Zone](#settings),
Username which is the `user_game_id` from the Auth Request,
Password which is the `password` from the Auth Request,
and auth_info, which is an [SFSObject](https://docs2x.smartfoxserver.com/api-docs/javadoc/server/com/smartfoxserver/v2/entities/data/SFSObject.html) with params\n

Token: which is the responded `token` from a request to **https://auth.bbbgame.net/auth/api/token/** with most params being the response from the original Auth Request.\n
Access Key which is a hardcoded key inside the My Singing Monsters EXE.
Client Version which is the [current version of My Singing Monsters](https://mysingingmonsters.fandom.com/wiki/Version_History).

After all of this, you should be logged into the MSM Servers now.
> [!IMPORTANT]
> You will need to click Login every few minutes to ensure you don't get kicked for being idle.

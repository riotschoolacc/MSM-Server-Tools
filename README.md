# MSM Server Tools
Tools for interacting with the MSM (My Singing Monsters) Servers made with ease of use in mind.

### Use cases:
* Making a custom client for My Singing Monsters
* Downloading your player data
* Learning about the way MSMs servers work
* Just for fun

### Do NOT use this program to
* DDos MSM Servers (as it is a ***[Cyber Crime](https://www.fbi.gov/contact-us/field-offices/anchorage/fbi-intensify-efforts-to-combat-illegal-ddos-attacks)***).
* Do any harm to account data, servers, BBB employees, etc
* Leak account data, upcoming updates, etc
* Do anything that may seem illegal

## Links:

[Settings](#settings)
[Authorization](#authorization)
[Login](#login)
[Loading Screen](#loading-screen)
[Requests](#requests)

**Legal**

[License](https://github.com/riotschoolacc/MSM-Server-Tools/blob/main/LICENSE)
[Security](https://github.com/riotschoolacc/MSM-Server-Tools/blob/main/SECURITY.md)

Settings
------
In MSM Server Tools there are multiple settings you can customize.

For example, if you want to connect to your own custom server, set the custom server ip to, for example, `127.0.0.1` (localhost), *default: `null`*.

Or, you can set your port to what your server supports, *default: `9933`*.

You can find a full list of settings **[here](#list-of-settings).**

> [!TIP]
> You should keep all the *Main* Settings the same to avoid problems.

Authorization
------
In My Singing Monsters, before anything happens, the client sends a request to **https://auth.bbbgame.net/auth/api/token/**.

Which in turn will send back:

* your User Game ID (`user_game_id`)
* And most importantly, your *authorization token* (`token`). 

Yu will click Authorization before you can do anything else and it'll create a new account by sending a request to **https//auth.bbbgame.net/auth/api/anon_account** which creates a new *anonymous* account, and responds with a Username, Password, Account ID, User Game ID & Authorization Token. 

I'm not sure why there's 3 things for account identification (*Account ID, User Game ID, & Username*).

One of the params MSM sends to the URL is `g` (Game ID)

| Game | ID |
| --- | --- |
| MSM Mobile | `1` |
| MSM Steam | `27` |

another is `t` (Login Type)

| Login Type | ID |
| --- | --- |
| Email | `email` |
| Anonymous | `anon` |
| Game Center | `gc` |

> [!CAUTION]
> Creating too many accounts in a short time period (around 1000, from experience) **will** get you IP Banned from the My Singing Monsters servers for a couple of minutes.
> But don't worry, you will be unbanned after around (from experience) 7 minutes.

Oddly enough, it doesn't check how many accounts you've created on that IP if you aren't on the mobile servers. But if you are using the mobile servers, it does check and refuses to allow you to create more if you have multiple.

Pregame Setup
------
After Authentication, the client sends a request to **https://msmpc.bbbgame.net/pregame_setup.php** with one param being the returned Auth Token from earlier. 

(mobile: **https://msm-auth.bbbgame.net/pregame_setup.php**)

Which in turn gives you one of the many Server IPs (`server_ip`) that MSM uses and an Update/DLC Files URL (`content_url`).

Login
------
Once the Server IP is located, you should in MSM Server Tools click *Server Login* which uses a wonderful [Smartfox2x implementation](https://github.com/MSM-Hacks/pyfox2x) made by **[MSM Hacks](https://github.com/MSM-Hacks)**
to connect to the Server using the responded IP *or [Custom Server IP](#settings)* and port `9933` *or the [Custom Server Port](#settings)*. If it is successful, MSM Server Tools should send a Login Request to the server

with params:

| Name | Description | Type |
| --- | --- | --- |
| `zone` | `My Singing Monsters` or your [Custom Zone](#settings) | `Utf-String` |
| `username` | the `user_game_id` from the Auth Request | `Utf-String` |
| `password` | the `password` from the Auth Request | `Utf-String` |

* and `auth_info`, which is an [SFSObject](https://docs2x.smartfoxserver.com/api-docs/javadoc/server/com/smartfoxserver/v2/entities/data/SFSObject.html) with params:

| Name | Description | Type |
| --- | --- | --- |
| `token` | the responded `token` from a request to **https://auth.bbbgame.net/auth/api/token/** | `Utf-String` |
| `access_key` | a hardcoded key inside the My Singing Monsters EXE. | `Utf-String` |
| `client_version` | the [current version of My Singing Monsters](https://mysingingmonsters.fandom.com/wiki/Version_History). | `Utf-String` |

[*English Documentation of PyFox2x*](https://github.com/mlnitoon2/pyfox2x)

> [!WARNING]
> You will need to click Login every few minutes to ensure you don't get kicked for being idle

Loading Screen
------
To be able to do any ingame (*after loading screen*) requests you have to go through the Loading Screen requests (for some reason, or else it yields on requests that aren't in the Loading Screen). 

So, you can automatically do it without the hassle of manually typing all the request commands by clicking Loading Screen! You are given the option to download all responses into a folder if you would like.

Afterwards, you can do any request.

Requests
------
My Singing Monsters uses [Smartfox2x](https://www.smartfoxserver.com/products/sfs2x) as their Client-Server structure, which allows for easy request sending and responding.

In MSM Server Tools, after you [Login](#login) you are given 5 new elements to play with:

* Request Name (You can find a list of all requests MSM requests and retrieves [here](https://github.com/riotschoolacc/MSM-Server-Tools/blob/main/requests.md)

* Params
*  All params are required to be inputted as JSON which MSM Server Tools will convert to an SFSObject and send to the servers. To specifically state which param should be which type (ex: Int, Double, String, Bool, etc) add the lowercase of it in the name. For example, if you want to send "monster_id" as an int, you should make your params look like this: `{"(int)monster_id": 3}`. Don't worry, it'll remove it from the string once its parsed.

* Send (Wait)
  * Send a request and wait for a response. (Will timeout and disconnect based on your [settings](#settings) if not responded by then.) Usually used for retrieving game Databases in the loading screen such as `db_monster` which sends the user all Monster Databases.
  * Will log in the logs textbox the response once you get one.

* Send (No Wait)
  * Send a request without waiting for a response. You should usually use this for actions such as `gs_update_structure` which updates a structure via the sent param `user_structure_id`.
  * You should only use *No Wait* if you aren't going to use the response.

* Loading Screen
  * [*Main section*](#loading-screen)

You need to click Loading Screen before doing any in-game requests!
 
For more information on how requests work, check out [the documentation of PyFox2x](https://github.com/MSM-Hacks/pyfox2x).

[*English Documentation of PyFox2x*](https://github.com/mlnitoon2/pyfox2x)

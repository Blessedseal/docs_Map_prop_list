---
description: Remote server management with RCON
---

# RCON

RCON allows administration of an R5Reloaded game server via remote console access.

{% hint style="danger" %}
You must make effort to keep your server secure, this means you should not share your RCON password or encryption key with anyone you don't absolutely trust, you should also consider if you really need to open RCON to the outside internet, if you don't you should not open any game server ports on TCP.
{% endhint %}

{% hint style="warning" %}
R5Reloaded does not accept any responsibility for unauthorized server access due to insecure RCON configuration.
{% endhint %}

## Prerequisites

* You must set a password for RCON to be enabled, you should set this in the relevant configuration file for your usage, these are found in the `platform/cfg/tools` folder of your R5Reloaded server, normally the `rcon_server` configuration file is used unless you launched with `-devsdk` or with the "Enable development" toggle enabled in the launcher, in this case the `rcon_server_dev` file is used.
* If you intend to allow RCON access from outside of your network you must open the TCP port on which the game server is running on, for ease of use when hosting multiple servers we recommend opening the range of 37015 - 37020.
* You should consider adding the IP address you intend to access the server from to the whitelist by setting `sv_rcon_whitelistaddress` to your IP, this will ensure that you cannot get locked out of your server when connecting from a trusted address.
* You may also wish to specify a specific encryption key to use via the `rcon_key` option in the RCON configuration file, this can make logging into a server much easier as the key does not need to be saved from the server console after every launch to log in with RCON. \
  This key must be a valid Base64 encoded AES-128 key, if you don't know what this means it is recommended you allow the server to generate a key and then input that as the saved key.

You will know RCON is successfully configured when you see "Remote server access initialized" in the game server console.

### Connecting to the server

Once you have configured the server to use RCON there are two ways of accessing the remote console.

### 1. Using netcon

Netcon can be found in the bin folder of your R5Reloaded install folder. In order to connect to your server you must specify the IP address, port and encryption key of your server, these should be specified in the format of `[IP]:Port Key`

Example: \[::ffff:127.0.0.1]:37015 WDNWLmJYQ2ZlM0VoTid3Yg==

{% hint style="info" %}
The IP address must be either an IPv6 address or an IPv4 address in IPv6 notation as shown above.
{% endhint %}

{% hint style="info" %}
The key is not what you would use to connect to the game server, this is the key you set in the `rcon_server` configuration file on the server, if you did not set a key you can get this from the server console.
{% endhint %}

Once you are connected to the server, you will need to authenticate using your password you configured in the RCON configuration files to do this you will need to run `PASS passwordhere` replacing "passwordhere" with your password.

Once this is done you should be able to execute commands as if you were using the console on the server itself.

### 2. Using the game client

In order to connect to a server over RCON from a game client you must set two ConVars. You may set these either via the console, or via the rcon\_client and rcon\_client\_dev files found in the `platform/cfg/tools` folder inside your R5Reloaded install.

| Name              | Note                                                            | Example                   |
| ----------------- | --------------------------------------------------------------- | ------------------------- |
| cl\_rcon\_address | Set to the IP address and port of the server you want to access | \[::ffff:127.0.0.1]:37015 |
| rcon\_key         | Set to the encryption key specified in your RCON server config  | WDNWLmJYQ2ZlM0VoTid3Yg==  |

{% hint style="info" %}
The rcon\_key is not what you would use to connect to the game server, this is the key you set in the `rcon_server` configuration file on the server, if you did not set a key you can get this from the server console.
{% endhint %}

After these ConVars are set you will need to authenticate, when you want to issue a command over RCON you must prefix the command with `rcon`, this will mean that in order to authenticate you will run `rcon PASS passwordhere` replacing "passwordhere" with your configured password. \
After this is complete you should see the message of `Netcon(X):Authentication successful.` after this you are ready to start issuing commands to the server.

{% hint style="info" %}
You must prefix any and all commands you want to execute on the remote server with `rcon` e.g. to launch a playlist you would run `rcon launchplaylist survival_dev`
{% endhint %}

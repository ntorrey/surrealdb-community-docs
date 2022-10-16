# Running SurrealDB in fly.io

1. Make a folder called `surrealdbdeployment` or something like that. Then make a new file in there called `Dockerfile` with no extension.
2.  Paste this in the file:

    ```
    FROM surrealdb/surrealdb:latest   (or 'FROM surrealdb/surrealdb:nightly')
    EXPOSE 8080
    CMD ["start", "--user","root","--pass", "yourpass",  "--bind","0.0.0.0:8080", "file://data/srdb.db"]
    ```

    By default surrealdb runs on port 8000 but fly forwards port 8080 by default to the 443 https port
3. Replace 'yourpass' with something long and secure..
4.  Then run `fly launch` and when it asks for a name type something you will use as the hostname.. which will then be used for your url like `https://myhostname.fly.dev/rpc` for your surrealdb instance. When it asks if you want to deploy **dont say yes**. then run `fly volumes create data --region [region-code-here] --size 1` for the region use the 3 letter code for where you chose to deploy, best is closest to you or where most of your users will be so the network latency is minimized. This creates a volume called data that is 1GB which you can extend later. Then you will see it created a file called `fly.toml.` Edit this file and add this at the end, no tabs or indentations. Just like this:

    ```
    [mounts]
    source="data"
    destination="/data"
    ```

    You can then run `fly deploy` if you want to deploy again
5. By default surrealdb runs on port 8000 but fly forwards port 8080 by default to the 443 https port
6. To keep it up to date you can set it to use `nightly` instead of `latest` in the dockerfile. Then you can just rerun fly deploy. You could also schedule this as part of a CICD build step in a git repo.

## Exporting/Downloading database file

(These steps are incomplete. Haven't figured this out yet. Hopefully it will be possible in the future to get the contents of the database through code - there is a feature request for this already).

1. Download the WireGuard app from [https://www.wireguard.com/install/](https://www.wireguard.com/install/)
2. In your terminal, navigate to the path of your fly.io configuration and run `flyctl wireguard create`.
3. Give a name for the WireGuard config file, ending with '.conf' (make sure it's less than 15 characters - this is the maximum length for an interface name on "Linux).
4. Now, from the WireGuard app, import the config file and click 'Activate' to bring the tunnel online.
5. Now, back in your terminal, run `flyctl ssh issue --agent personal`  and enter your email.

Source https://discord.com/channels/902568124350599239/1022387563627028511

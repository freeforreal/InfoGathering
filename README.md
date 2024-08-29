# Info Gathering of a Discord user

> **To get information from a Discord user, I recommend the following steps (please note that all of this is a dispensable and modifiable example):**

**1. Activate the Discord developper mode**

```text
User Settings > Application Settings > Behaviour and enable Developer Mode
```

**2. Obtain the user ID of the person to be provided with information** 

```text
Right click in the username > Copy user ID
```

**3. Obtaint information from this ID**

- **For this step we will use the API of [this](https://github.com/mesalytic/discord-lookup-api) repository, which can also look up information about guilds, apps, etc... But we will use it to look up the person ID of the user**

```text
https://discordlookup.mesalytic.moe/v1/user/ + the user ID of the person to search
```

- **The search result in your browser should look something like this:**

![imagen](https://github.com/user-attachments/assets/826ca3e5-79b4-4b53-a184-c2cbefacd3f5)

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

> **Here is an example of a Python request to the API to automate the process:**

```python
import requests, os

def clear():
    if os.name == 'nt': os.system('cls')
    else: os.system('clear')

API_URL = 'https://discordlookup.mesalytic.moe/v1/user/'

def main():
    clear()
    user = int(input('Enter the user ID to gather information: '))
    try:
        response = requests.get(API_URL + str(user))

        if response.status_code == 200:
            data = response.json()
                
            def format_user_info(data, indent=0):
                info = []
                for key, value in data.items():
                    if isinstance(value, dict):
                        info.append("  " * indent + f"{key.replace('_', ' ').title()}:")
                        info.append(format_user_info(value, indent + 1))
                    else:
                        if isinstance(value, list):
                            value = ", ".join(str(v) for v in value)
                        info.append("  " * indent + f"{key.replace('_', ' ').title()}: {value}")
                return '\n'.join(info)
                
            user_info = format_user_info(data)
            print('\n-------------------------------------------------------------------------------')
            print(user_info)
            print('\n-------------------------------------------------------------------------------')

        input()
        main()

    except Exception as ex:
        print('Error: ' + str(ex))


if __name__ == '__main__':
    main()
```

**4. Okay, after this, let's put social engineering into practice to get the target person's PayPal**

-  **You can send a message like this:**

```text
Hi, I would like to buy some items from your shop, I have been looking for them for a long time and I have found them, please tell me the price!
```

> **This is an example message, you can use any message you want**

- **Paypal example:**

```text
paypal.me/username
```

- **This is the structure if paypal.me, the most common, but the user can provide you the email**

- **Example PayPal email:**

```text
example@gmail.com
```

**5. When you have PayPal.me, we will use my server tech, which you can access [here](https://discord.gg/freeforreal)**

- You need to get the tech from the shop called ‘t2ch-paypal’

![imagen](https://github.com/user-attachments/assets/1ec41666-d86e-479e-bb66-7dbdde011486)

**6. Use the tech to get the person's email and phone number. The number may not be revealed, there is a bug for that, but get as much information as you can from that PayPal**

**6. After that, you can use our bots for server lookups, as well as other platforms such as intelX. I also recommend you to use the snusbase tool you will find on my server to check if the email is leaked**

> **Para el número de teléfono, te recomiendo esta [herramienta](https://github.com/Euronymou5/Dark-Hydro)**
> **For email, I re-recommend these sites, in addition to open source tools from GitHub that you can download and use, like [MailCat](https://github.com/sharsil/mailcat) or [Sherlock](https://github.com/sherlock-project/sherlock), for example:**

- https://mailmeteor.com/email-checker
- https://www.aware-online.com/en/osint-tools/email-address-tools/
- https://epieos.com/
- https://hunter.io/email-verifier
- https://tools.emailhippo.com/
- https://email-checker.net/

> **If you want to make more complete OSINT searches, I recommend [this](https://github.com/Euronymou5/DorkBuster) tool**

#### Obtaining the public IP

**1. If you want to get someone's public IP, the first option is [IpLogger](https://iplogger.org/en/) (in my opinion the worst)**
**2. The second option is to use the open source tool [RedHawk](https://github.com/Tuhinshubhra/RED_HAWK). You can download it by following the instructions, and it allows you, among other options, to know the public IP of the user who has raised a website. In other words, if the target has a website, this tool is generally very useful**
**3. The last option is to create your own website and host it (on [GitHub Pages](https://pages.github.com/) or another hosting of your choice) and put the code shown below:**


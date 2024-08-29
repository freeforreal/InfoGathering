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

> **Here is an example of a python request to the API to automate the process:**

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

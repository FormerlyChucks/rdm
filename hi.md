# snippets
A collection of my Python snippets

## Converting utc

To convert utc to date format:

(`created_utc` will have to be an integer)

```python
import time
created_utc = 
date = time.strftime("%D", time.gmtime(created_utc))
print(date)
```

To convert utc to days:

```python
import time
from datetime import datetime, timedelta

created_utc = 
print((datetime.utcnow() - datetime.utcfromtimestamp(created_utc)).days)
```

## Downloading something

Downloading something is fairly easy:

(We will be downloading my profile picture)

```python
import requests

response = requests.get("https://avatars1.githubusercontent.com/u/61555147")

file = open("profile-pic.png", "wb")
file.write(response.content)
file.close()
```

You might not be able to, as the default header is rate-limited a lot. Simply add a header like this:

```python
headers = {'User-agent': 'this is your user-agent'}
response = requests.get("https://avatars1.githubusercontent.com/u/61555147", headers=headers)
```

Sometimes, we need to get text, like with JSON:

(we will be getting data from api.github.com)
```python
response = requests.get("https://api.github.com/").text
print(response)
```

## To open a file and write some text:

```python
with open("file.ext", "r") as file:
    f.write("Example Text")
```
You should adjust the last line like this:
```python
f.write("Example Text" + "\n")
```
Otherwise trying to run it again will look like this:

    ExampleTextExampleText

## Want to choose a random string from a list? Just use this:
```python
import random

choices = ['1', '2', '3']
print(random.choice(choices))
```

## Loading JSON data:

Its pretty easy:

```python
import requests, json

json_loaded = json.loads(requests.get('https://api.github.com').text)
print(json_loaded["current_user_url"])
```

## Need to ask a question?

```python
q = input("What is your name")
print("Hello, " + q)
```

## Getting the current time

```python
from datetime import datetime

print(datetime.now().strftime("%H:%M"))
```
That will return something like this:

    13:29

To get the seconds as well:

```python
from datetime import datetime

print(datetime.now().strftime("%H:%M:%S"))
```

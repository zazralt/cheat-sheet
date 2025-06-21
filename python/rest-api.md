
# REST API

# Flask Server

# Request Methods

```python

import requests

# Base URL and Headers
BASE_URL = 'https://httpbin.org/'
headers = {
    'Authorization': 'Bearer YOUR_TOKEN',
    'Content-Type': 'application/json'
}

# GET Request (read)
response = requests.get(f'{BASE_URL}/get', headers=headers)

# POST Request (create)
data = {'name': 'Zaz'}
response = requests.post(f'{BASE_URL}/post', headers=headers, json=data)

# PUT Request (create or update)
data = {'name': 'Zaz New'}
response = requests.put(f'{BASE_URL}/put', headers=headers, json=data)

# PATCH Request (update)
data = {'name': 'Zaz Updated'}
response = requests.patch(f'{BASE_URL}/patch', headers=headers, json=data)

# DELETE Request
response = requests.delete(f'{BASE_URL}/delete', headers=headers)

# view response content
print(response.json())

# view status code
print(response.status_code)

```

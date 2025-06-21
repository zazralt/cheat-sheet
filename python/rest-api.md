
# REST API

# Flask Server

# Request Methods

```python

import requests

# Base URL and Headers
BASE_URL = 'https://api.example.com'
headers = {
    'Authorization': 'Bearer YOUR_TOKEN',
    'Content-Type': 'application/json'  # Ensure proper content-type for JSON APIs
}

# GET Request
response = requests.get(f'{BASE_URL}/data', headers=headers)
print("GET response:", response.json())

# POST Request
data = {'name': 'Zaz'}
response = requests.post(f'{BASE_URL}/users', headers=headers, json=data)
print("POST response:", response.status_code, response.text)

# PATCH Request
patch_data = {'name': 'Zaz Updated'}
response = requests.patch(f'{BASE_URL}/users', headers=headers, json=patch_data)
print("PATCH response:", response.status_code, response.text)

# DELETE Request
response = requests.delete(f'{BASE_URL}/users', headers=headers)
print("DELETE response:", response.status_code, response.text)

```

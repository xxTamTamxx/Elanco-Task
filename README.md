# Elanco-Task
import requests

import json

res= requests.get('https://engineering-task.elancoapps.com/api/raw')

print(res.json())

with open('ElancoRaww','w') as json_file:

    json.dump(res.json(), json_file)

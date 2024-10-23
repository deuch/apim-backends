# APIM Backends pool creation

This repo contains a json file in ARM format to create backend and backend pools in an existing APIM

# How to use

You need to set those parameters :

| Parameter | Value | Note |
| --- | --- | ------------- |
|APIM Name||Specifies the name of the APIM.|
|backendList||Array of backend to create in the APIM. Pattern, an Array [] of multiple {"backendName": "Name of the backend" (must be unique), "url": "backend url", "weight": value, "priority": value}| 
|backendPoolName||Name of the backend pool|

For example of the backendList :



<code>[
    {"backendName": "backend-1", "url": "https://backend-1.azure.openai.com/openai", "weight": 80, "priority": 1},  
    {"backendName": "backend-2", "url": "https://backend-2.azure.openai.com/openai", "weight": 20, "priority": 1}   
]</code>

You can set weight at 100 and priority at 1 to have a round robin load balancing.

[![Deploy To Azure](https://raw.githubusercontent.com/deuch/apim-backends/master/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fdeuch%2Fapim-backends%2Frefs%2Fheads%2Fmain%2Fdeploy.json)

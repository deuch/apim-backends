# APIM Backends pool creation

This repo contains a json file in ARM format to create backend and backend pools in an existing APIM

# How to use

You need to set those parameters :

| Parameter | Optional | Note |
| --- | --- | ------------- |
|APIM Name|No|Specifies the name of the APIM.|
|backendList|No|Array of backend to create in the APIM. Pattern, an Array [] of multiple {"backendName": "Name of the backend" (must be unique), "url": "backend url", "weight": value (optional), "priority": value (optional)}| 
|backendPoolName|No|Name of the backend pool|
|EntityKey|No|Name of Key to retrieve the pool in the JSON List|
|APIMBackendNamedValue|No|Name of the Named Value of the APIM that host the list of EntityKey:BackendPoolName|

For example of the backendList :

<code>[
    {"backendName": "backend-1", "url": "https://backend-1.azure.openai.com/openai", "weight": 80, "priority": 1},  
    {"backendName": "backend-2", "url": "https://backend-2.azure.openai.com/openai", "weight": 20, "priority": 1}   
]</code>

or without weight and priority (round robin is applied) :  

<code>[
    {"backendName": "backend-1", "url": "https://backend-1.azure.openai.com/openai"},  
    {"backendName": "backend-2", "url": "https://backend-2.azure.openai.com/openai"}   
]</code>

You can set weight at 100 and priority at 1 to have a round robin load balancing. Or your can ommit priority and weight.

For the JSON stored in the Named Value in APIMn you need to use this format :

<code>{ "entityKey1": "backendPoolName1", "entityKey2": "backendPoolName2"}
</code>

The script will create the new pair EntityKey:BackendPoolName or update an existing one.

[![Deploy To Azure](https://raw.githubusercontent.com/deuch/apim-backends/master/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fdeuch%2Fapim-backends%2Frefs%2Fheads%2Fmain%2Fdeploy.json)

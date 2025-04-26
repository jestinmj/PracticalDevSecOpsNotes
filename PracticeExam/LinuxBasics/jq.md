learn to filter and transform json data. jq is like sed for JSON data. AN eloquent command line processor tool to filter and transform your JSON with ease

jq uses filters

can apply jq to json string, API response or json file

.[] iterates over each element of the array form the response, one at a time

iterate over each element:

```
jq '.[] | .details' learnjq.json
```

chain property values

```
jq '.[] | {name: .details.name, url:.details.url}' learnjq.json
```

Access single array item

```
jq '.[1] | {name: .details.name, url: .details.url}' learnjq.json
```

Put results in an array

```
jq '[.[] | {name: .details.name, url: .details.url}]' learnjq.js
```


Next let us try getting services property from learnjq.json data. If you watch closely, the services property is an array. We already know now that to access array, we have to use 
`jq '.[] | {name: .details.name, url: .details.url, services: .services[]}' learnjq.json`

We now have the services property and its values. But did you notice that for each cloud provider, it shows up the result twice? How would you change this so that it groups the services for each service provider? We already learned above that you have to wrap the square bracket in order to get the result in a single array. So let’s wrap the .services into a single array to get you the desired result.
`jq '.[] | {name: .details.name, url: .details.url, services: [.services[]]}' learnjq.json`
Alternatively, we can use the following command, which produces similar output as the one above
`jq '.[] | {name: .details.name, url: .details.url, services: .services}' learnjq.json`



jq functions:

length returns length of input

```
jq '.[] | {name: .details.name, servicecount: .services | length}' learnjq.json
```

select based on a condition  

```
jq '.[] | select(.details.name=="AWS")' learnjq.json
```

Access something within a file  

```
jq ".[0].summary.failed" /terraform/scan-result.json
```

Access a key with a . in it

```
cat example.json | jq .example.'"thing.with.dot"'
```

How would you display the results for a cloud provider that has CI-CD service. Use the learnjq.json file and try to write the jq filter.
`jq '.[] | select(.services[].type=="CI-CD") | .details.name' learnjq.json`
`jq '.[].services[] | select(.type=="CI-CD")' learnjq.json`
`jq '.[].services[] | select(.type=="CI-CD") | .name' learnjq.json`


1. How would you filter the cloud provider name that has CI-CD service in the learnjq.json file.
   `jq '.[] | select(.services[].type=="CI-CD") | .details.name' learnjq.json`
2. Show us the result of CI/CD service name that provided by each cloud provider.
   `jq '.[].services[] | select(.type=="CI-CD") | .name' learnjq.json`

Chuck Norris

```Groovy
groovy:000> import groovy.json.JsonSlurper
groovy:000> BASE = 'http://api.icndb.com/jokes/random?'
groovy:000> new JsonSlurper().parseText("${BASE}qs".toURL().text).value.joke
```

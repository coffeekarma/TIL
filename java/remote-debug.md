# Remote debug an external java application

To remote debug any external java application start the jvm with the following parameters (port can be changed as desired): 

```
-Xdebug -Xnoagent -Djava.compiler=NONE -Xrunjdwp:transport=dt_socket,address=8989,server=y,suspend=y
``` 

### JNLP-Debug:
Most convenient way if using eclipse: create an "external tools configuration" with the parameters and set ${string_prompt:JNLP-Url:https://} as argument. 

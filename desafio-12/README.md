
# Desafio 12 Coderhouse

Informaci贸n adicional sobre el desafio de balanceador de carga

# Aspectos a considerar 馃様
+ Al iniciar **pm2** con el comando ```pm2 start ./process.json``` 贸 ```pm2 start src/app.js -- --port=8081 --modo=CLUSTER``` se abren pesta帽as de node en el equipo dependiendo de los nucleos del PC, no as铆 cuando solo se ejecuta desde **node**.
+ En el archivo de configuraci贸n levantar las instacias con el parametro adicional ```"exec_mode": "cluster"``` si bien deja arriba las instancias con pm2 no es posible conectarse desde **nginx**. 驴Se requiere alguna configuraci贸n adicional?
+ Si bien se trato de realizar lo solicitado en el enunciado al realizar las pruebas estos funcionaban de forma correcta (aun as铆 me quedan algunas dudas en unos puntos).
+ **El proyecto lo realice desde mi trabajo donde no pude liberar el puerto 80, es por esto que el archivo de nginx y configuraci贸n process.json comienzan desde el puerto 8080. 馃槀**

# Comandos de ejecuci贸n
#### Comandos para ejecutar aplicaci贸n sin pm2
+ Ejecuci贸n en modo **cluster**: ```node src/app.js --port=8081 --modo=CLUSTER```
+ Ejecuci贸n en modo **fork**: ```node src/app.js --port=8081 --modo=FORK```

#### Comandos para ejecutar aplicacion **con** pm2
+ ```pm2 start ./process.json``` 猬咃笍 **Ejecuci贸n dentro de la carpeta del proyecto**

#### Comandos para detener procesos de pm2
+ ```pm2 delete all```

# Configuraci贸n archivo [process.json](https://github.com/jcandiap/desafio-12-coderhouse/blob/main/process.json)
# Todos estos son los casos presentados dentro del desafio 馃憖

#### Para configurar un servidor con 2 instancias en modo **fork**
```json
    {
        "apps": [
            {
                "name": "Process 8081",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8081 --modo=FORK"
            },
            {
                "name": "Process 8082",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8082 --modo=FORK"
            }
        ]
    }
```

#### Para configurar un servidor con 5 instancias en modo **fork**
```json
    {
        "apps": [
            {
                "name": "Process 8081",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8081 --modo=FORK"
            },
            {
                "name": "Process 8082",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8082 --modo=FORK"
            },
            {
                "name": "Process 8083",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8083 --modo=FORK"
            },
            {
                "name": "Process 8084",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8084 --modo=FORK"
            },
            {
                "name": "Process 8085",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8085 --modo=FORK"
            }
        ]
    }
```

#### Para configurar un servidor con 5 instancias en modo **cluster**
```json
    {
        "apps": [
            {
                "name": "Process 8081",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8081 --modo=CLUSTER"
            },
            {
                "name": "Process 8082",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8082 --modo=CLUSTER"
            },
            {
                "name": "Process 8083",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8083 --modo=CLUSTER"
            },
            {
                "name": "Process 8084",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8084 --modo=CLUSTER"
            },
            {
                "name": "Process 8085",
                "script": "src/app.js",
                "watch": true,
                "args": "--port=8085 --modo=CLUSTER"
            }
        ]
    }
```

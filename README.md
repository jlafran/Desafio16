# Desafio 15
Steps para pruebas de carga y profiling:

## Ejecutar los comandos, en orden:
1) ### node --prof src/index.js 
Para generar el archivo isolate.log
Ese archivo lo renombre a conClog.log

2) ### artillery quick --count 50 -n 20 "http://localhost:8080/api/info" > profilingConConsoleLog.txt 
50 usuarios, 20 request

3) ### node --prof-process conCLog.log > result_profConCLog.txt
Genero el txt que me permite ver, por ejemplo, en summary, la cantidad de ticks. Cuanto menos ticks haya, mejor rendimiento

5) ### pm2 start src/index.js --name api8084 --watch -- --port 8084

7) ### pm2 start src/index.js --name api8085 --watch -- --port 8085

##Test de carga
Para hacer los test en el codigo con y sin console.log, lo que hice fue comentar/descomentar las lineas correspondientes en el archivo info.controllers.js
1) ### npm run startCarga 
Tengo configurado ese script en el package.json

2) ### npm run testCarga

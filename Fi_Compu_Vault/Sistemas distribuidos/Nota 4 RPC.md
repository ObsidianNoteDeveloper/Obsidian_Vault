Llamadas de procedimiento remoto

#### Algunos puntos problemáticos del RPC son:

1. Se deben de usar espacios de direcciones distintos, debido a que se ejecutan en computadoras diferentes.
2. Como las computadoras pueden no ser idénticas, la transferencia de parámetros y resultados pueden complicarse
3. Ambas computadoras pueden descomponerse


#### Modo de operación del RCP:

La llamada a un procedimiento remoto considera los siguientes pasos:
1. El procedimiento cliente llama al resguardo del cliente de la manera usual 
2. El resguardo del cliente construye un mensaje y realiza un señalamiento al núcleo.
3. El núcleo envía el mensaje al núcleo remoto
4. El núcleo remoto proporciona el mensaje al resguardo del servidor
5. El resguardo del servidor desempaca los parámetros y llama al servidor 
6. El servidor realiza el trabajo y regresa el resultado al resguardo 
7. El resguardo del servidor empaca el resultado en un mensaje y hace un señalamiento mediante el núcleo
8. El núcleo remoto envía el mensaje al núcleo del cliente 
9. EL núcleo del cliente da el mensaje al resguardo del cliente
10. El resguardo desempaca el resultado y lo entrega al cliente

![](ModoOperacionRPC.png)




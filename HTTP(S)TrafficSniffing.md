Esta práctica pretende demostrar la diferencia entre sniffear tráfico HTTP y HTTPS.

Se abre wireshark: 
- wireshark -i eth1  para iniciar wireshark en la interface eth1

Nos dan un usuario y contraseña: 
bee y bug respectivamente

![image](https://user-images.githubusercontent.com/44788583/151722407-701d59c8-3fad-4b73-ad2c-3ae0a69e5a91.png)

Tenemos dos páginas muestra en la vpn:
- demo.ine.local
- demossl.ine.local

![image](https://user-images.githubusercontent.com/44788583/151722437-9aafdd77-45a5-4125-9e36-050bb7fa4072.png)

### Prueba con http sin encriptación

Dentro de demo.ine.local: 

Se tiene un formulario de usuario y contraseña, se envían ambos correctamente:
Se hace el login correctamente y en wireshark se hace click a uno de los paquetes y se selecciona la opción follow tcp stream:

![image](https://user-images.githubusercontent.com/44788583/151722629-d4362188-c8fb-45b8-b331-f4692eb5b51a.png)

Podemos ver claramente que el usuario era bee y la contraseña bug

![image](https://user-images.githubusercontent.com/44788583/151722647-c0a86f57-ef54-4753-afb1-3cd4b6e7146f.png)

Ahora repetimos el proceso pero con credenciales no válidas:

![image](https://user-images.githubusercontent.com/44788583/151722676-6cbc2481-a64c-4cd0-821d-102577725acc.png)

Podemos ver el usuario fake como usuario y la contraseña elegida.

![image](https://user-images.githubusercontent.com/44788583/151722696-254b219f-ba31-4a5b-a26b-d8f9c73fab77.png)

-----

### Prueba con HTTPS

Iniciamos con bee y bug (Credenciales correctas) y vemos que se hace el login correcto

![image](https://user-images.githubusercontent.com/44788583/151722721-5141873d-3eb6-4934-9d36-59c83bcde24e.png)

Checamos el tcp stream pero no podemos ver las credenciales enviadas


![image](https://user-images.githubusercontent.com/44788583/151722731-b3ce155d-210e-4063-aaac-73d19bac1bce.png)

Repetimos el proceso con credenciales inválidas

![image](https://user-images.githubusercontent.com/44788583/151722762-42503b16-678b-4280-8fd1-23621faf5091.png)

y tampoco podemos ver lo que se envió. El hecho de que haga login o no, no afecta en la encriptación de la comunicación.



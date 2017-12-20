# VideoChat con PeerJs y NodeJs

## Requerimientos
* Node >= 6 (Para la prueba use Node 6.10.0) 
* NPM >= 5 (Para la prueba use NPM 5.6.0)

## Instalacion

1) Lo primero que debemos hacer para instalar y correr el videochat, es dirigirnos a la carpeta `public` desde la terminal y ejecutar el comando `npm install`

2) Luego nos dirigimos a la carpeta `server` desde la terminal y ejecutamos el comando `npm install`

## Correr el servidor

1) En estos momentos, debemos correr dos servidores, primero tenemos que correr el servidor web que se encarga de montar la aplicacion para poder visualizar, para realizar esto, nos dirigimos a la carpeta `public` y corremos el comando `node website-server.js`, el servidor se ejecutara en `https://localhost` o en la direccion de IP actual del computador

1) Luego, abrimos otra terminal y debemos correr el servidor socket de `PeerJs` que se encarga del flujo de la informacion, para realizar esto, nos dirigimos a la carpeta `server` y corremos el comando `node peer-server.js`

## Configuracion 

Tenga en cuenta que para que la aplicacin se ejecute de forma correcta, desde el cliente debe establecer la direccion del socket al cual ud quiere conectar, en este caso, la direccion generada por el socket de `PeerJs`

Para realizar esto, en un editor de texto, abrimos el archivo ubicado en `public/index.html` y ubicar el siguiente codigo

<pre><code>
var peer = new Peer(username, {
    host: "localhost",
    port: 9000,
    path: '/peerjs',
    debug: 3,
    config: {
        'iceServers': [
            {
                url: 'stun:stun1.l.google.com:19302'
            },
            {
                url: 'turn:numb.viagenie.ca',
                credential: 'muazkh',
                username: 'webrtc@live.com'
            }
        ]
    }
});
</code></pre>

En el atributo `host`, sustituir por la direccion de IP actual del computador


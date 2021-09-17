# Juego: Tirar dados 🎲

👀 Juega aquí **https://dice-game-mx.netlify.app/**

## Instalación
1. Clona el repositorio y ubicandote dentro de la carpeta ejecuta (para la instalación de dependencias)
    ```
    npm install
    ```
    Si quieres correr el lint ejecuta:
    ```
    npm run lint
    ``` 
2. Una vez que termine de instalar dependencias, a continuación ejecuta (para levantar el servidor):
    ```
    npm run serve
    ```
    
3. Si haz hecho todo correctamente te aparecerá esta vista en consola y puedes entrar a tu local desde el navegador
  
![](https://i.imgur.com/8Bj8HKi.png)

### Vista inicial del juego

![](https://i.imgur.com/KBhiY5i.png)

### Gif funcionando
---
![](https://i.imgur.com/K51PTFY.gif)


⚠ **Reglas**
* El número minimo de dados que debe de existir es 1
* La cantidad máxima de caras es 20
* El maximo de dados que se puede agregar son 10
* Si agregas un número  de caras mayor a 6, el dado dejará de mostrar con puntos de colores y te arrojará el número.

🕹 **¿Qué puedo hacer?**
* Al iniciar el juego aparecerán dos dados inicializados en 1, por lo que puedes comenzar a girar y te darán dados entre el 1 y 6 que es el número de caras predeterminado.
* Puedes agregar más dados y todos los nuevos inician en 1 y si no haz modificado el número de caras serán entre 1 y 6.
* Si ya modificaste el lado de las caras, entonces tus siguientes tiros serán entre ese rango de números. 🧠 Recuerda que puedes agregar hasta 20 lados de caras.

🏆 **Y ¿cómo gano?**
* El juego de dados está diseñado para que puedas usarlo para reemplazar tu dado fisico. Así que tu victoria dependerá del juego para el cual lo uses.


## Análisis de la lógica aplicada
![](https://i.imgur.com/yiokLaf.png)
**https://miro.com/app/board/o9J_lFEkCCg=/**

### Plugins usados
1. @vue/cli-service v4.5.13
2. @vue/cli-plugin-babel 4.5.13
3. @vue/cli-plugin-eslint 4.5.13

### Dependencias
1. core-js v3.12.0
2. vue v3.0.11
3. Node v12.13.1

### Scripts
1. serve: vue-cli-service serve
2. build: vue-cli-service build
3. lint: vue-cli-service lint

### Lectura sobre los dados
**¿Cuántas caras puede tener un dado?**
Este juego esta basado en el numero de caras de un dado de equilibrio, pero puedes ingresar hasta un maximo de 20 caras que es la cantidad de caras que puede llegar a tener un poliedro regular. **https://es.wikipedia.org/wiki/Dado**

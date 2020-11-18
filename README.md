# Login-Netflix
Projecto Login Neflix de Juan Pablo de la torre

Creamos un package.json e instalamos las dependencias de gulp

`$ npm init`

`$ npm install --save-dev gulp gulp-autoprefixer gulp-sass`

Hacemos los mixins tenemos que añadirle dentro una directiva @ contente apra cuando compile va a ver el contenido que colocas en el media query y lo mete en la hoja de estilos.

```
$telefono: 480px;

@mixin telefono {
    @media (min-width: #{$telefono}) {
        @content;
    }
}
```

Para que los padding o un border cambien los tamaños de los elementos incluimos este mixin

```
@mixin box-sizing($box-model) {
    box-sizing: $box-model;
}
```

Y en el app.scss añadimos al html

```
html {
    @include box-sizing(border-box)
}
```
Después ponemo el sniper 

```
*,
*:after,
*:before{
    @include box-sizing(inherit);
}
```
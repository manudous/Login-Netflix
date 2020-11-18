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

Para conseguir el efecto que el label esté dentro del input hacemos esto

```
 .campo{
        display: flex;
        position: relative;
        margin-bottom: .8rem;
        label{
            position: absolute;
        }
```

A los inputs le cambiamos el color de fondo cuando hacemos un focus en el y quitamos la línea azul que rodea muchas veces a los imports

```
input{
            flex: 1;
            padding: 1.3rem 1rem .7rem 1rem;
            border: none;
            background-color: $gris;
            border-radius: $radius;
           + &:focus {
                background-color: $gris3;
               + outline: none;// Quitamos el borde que rodea.
            }
```

Lo siguiente que vamos a hacer es cuando pulsamos en alguno de los dos imports se hagan más pequeña la fuente y se coloque en un lugar distinto. 

```
input{
            flex: 1;
            padding: 1.3rem 1rem .7rem 1rem;
            border: none;
            background-color: $gris;
            border-radius: $radius;
            &:focus {
                background-color: $gris3;
                outline: none;

                + label {
                    font-size: .6rem;
                    top: .5rem;
                }
            }
        }
```
El + lo que hace es que si seleccióamos a ese label con el + se va al siguiente elementos por esto ponemos de esta forma en el html para poder seleccionarlo. Y nos haga el efecto de ponerse la fuente más pequeña y desplazarse.

```
<input type="text" id="usuario">
<label>Email o número de teléfono</label>
```

Le agregamos al label un efecto de transición

```
label{
    position: absolute;
    top: 1.1rem;
    left: 1rem;
   + transition: font-size .2s ease, top .2s ease;
}
```

Para poder agregarle estilos a un select hay que agregarle esta propiedad para luego poder darle el resto de propiedades.

```
 select{
       + appearance: none;
        padding: 1rem 3rem;
        border: 1px solid $gris3;
        border-radius: $radius;
        font-size: .8rem;
        background-color: $negro;
        color: $gris2;
    }
```
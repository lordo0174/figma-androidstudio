# Pantalla 4 · Carrito — A1 y A2

## A1 · Árbol de bloques

Leyenda:
- **[NP]** no se programa como vista (es un fondo, una sombra o una agrupación de Figma; pasa a ser un atributo o un drawable)
- **[SUP]** elemento superpuesto a otro
- **[REP]** estructura que se repite

```
4 - Carrito (frame, fondo blanco) ............................. ConstraintLayout raíz
├── Barra superior
│   ├── Flecha atrás .......................................... ImageButton
│   └── Cabecera
│       ├── Rectángulo verde menta, esquinas redondeadas ....... [NP] [SUP] fondo (drawable) del título
│       │   └── Sombra ......................................... [NP] efecto → android:elevation
│       └── Texto «Carrito» ................................... [SUP] TextView (encima del rectángulo)
├── Producto del carrito ...................................... [REP] fila de la lista: se repite por cada producto
│   ├── Foto de la camiseta (esquinas redondeadas) ............ ImageView
│   │   └── Máscara / fondo gris redondeado ................... [NP] [SUP] forma de recorte de la imagen
│   ├── Texto «Camiseta niño» ................................. TextView
│   ├── Texto «8,99 €» ........................................ TextView
│   ├── Texto «1» (cantidad) .................................. TextView
│   └── Icono papelera ........................................ ImageButton
├── Resumen del pedido
│   ├── Texto «Resumen del pedido» ............................ TextView
│   ├── Fila Subtotal ......................................... [REP] etiqueta a la izquierda + importe a la derecha
│   │   ├── «Subtotal» ........................................ TextView
│   │   └── «8,99 €» .......................................... TextView
│   ├── Fila Envío ............................................ [REP]
│   │   ├── «Envío» ........................................... TextView
│   │   └── «3,99 €» .......................................... TextView
│   └── Fila Total ............................................ [REP]
│       ├── «Total» ........................................... TextView
│       └── «13,99€» .......................................... TextView
├── Botón Checkout ............................................ Button (una sola vista)
│   ├── Rectángulo verde, esquinas redondeadas ................ [NP] [SUP] fondo del botón (backgroundTint + cornerRadius)
│   │   └── Sombra ............................................ [NP] efecto → elevation
│   └── Texto «Checkout» ...................................... [SUP] texto del propio botón
└── Barra de navegación inferior .............................. BottomNavigationView
    ├── Icono casa (Inicio) ................................... [REP] elemento del menú
    ├── Icono corazón (Favoritos) ............................. [REP] elemento del menú
    └── Icono persona (Perfil) ................................ [REP] elemento del menú
```

Comparación con el panel de capas: *(pendiente: falta ver el panel de capas de tu Figma)*

## A2 · Renombrado de capas en Figma

Con ViewBinding, el id `tv_titulo` se usa en Java como `binding.tvTitulo`.

| Capa actual (lo que es) | Nuevo nombre | Vista o recurso en Android |
|---|---|---|
| Frame «4 - Carrito» | `activity_carrito` | layout `activity_carrito.xml` |
| Flecha atrás | `ib_volver` | ImageButton · icono `ic_volver` |
| Rectángulo verde de la cabecera | `bg_cabecera` | drawable de fondo |
| Texto «Carrito» | `tv_titulo` | TextView |
| Grupo del producto | `item_carrito` | fila repetible |
| Foto de la camiseta | `iv_producto` | ImageView · foto `img_camiseta_nino` |
| Texto «Camiseta niño» | `tv_nombre_producto` | TextView |
| Texto «8,99 €» del producto | `tv_precio_producto` | TextView |
| Texto «1» | `tv_cantidad` | TextView |
| Papelera | `ib_eliminar` | ImageButton · icono `ic_eliminar` |
| Texto «Resumen del pedido» | `tv_resumen` | TextView |
| «Subtotal» / «8,99 €» | `tv_subtotal_etiqueta` / `tv_subtotal_valor` | TextView |
| «Envío» / «3,99 €» | `tv_envio_etiqueta` / `tv_envio_valor` | TextView |
| «Total» / «13,99€» | `tv_total_etiqueta` / `tv_total_valor` | TextView |
| Grupo del botón (rectángulo + texto) | `btn_checkout` | Button |
| Barra inferior | `bnv_navegacion` | BottomNavigationView |
| Icono casa | `nav_inicio` | elemento del menú · icono `ic_inicio` |
| Icono corazón | `nav_favoritos` | elemento del menú · icono `ic_favoritos` |
| Icono persona | `nav_perfil` | elemento del menú · icono `ic_perfil` |

Las capas **[NP]** (sombras, máscara de la foto, grupos que solo sirven para ordenar) se quedan sin prefijo de vista.

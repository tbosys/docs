Se puede crear cualquier tipo de App a mano, no hay limitaciones de ningun tipo.

Sin embargo hemos encontrado un formato interativo que funciona muy bien en la mayoria de los requerimientos de una app para empresas.

La apps de negocios funcionan muy bien basadas en el patron de tablas con filas y columnas tipo Excel, mezclado con acciones. Estas acciones son botones,
uno escoge una o varias filas y puede dar click en estos botones para ejecutar una accion.

Acciones pueden ser por ejemplo aprobar una compra, imprimir una factura, enviar un pedido. Iniciar un proceso relacionado a una o mas filas seleccionadas.

De la misma forma se pueden editar, crear y por supuesto ver los detalles de cada fila.

Se tiene acceso a todos los datos, aunque sea millones de facturas de los ultimos 10 años. Se pueden filtrar, agrupar y ordenarlos por columna.

Este patron, cumple con la gran mayoria de casos de negocios. Lo importante es contar con una experiencia de usuario excepcional para que al trabajar se sienta
como que esta utilizando el app mas avanzado del mundo en computadora, tablet o telefono mobil. Para que el uso de la tecnologia le permita hacer algo que antes no podia.

Para contar con un experiencia de usuario excepcional se han construido componentes especiales, pero tambien se ha disenado el sistema de una forma extendible que permite agregar funciones de inteligencia artificial, agregacion y carga automatica de datos relacionados.

Cuando se esta realizando una accion, por ejemplo realizando una venta es comun que se tengan que realizar tareas paralelas. Por ejemplo crear un cliente nuevo, el sistema esta disenado de una forma que no require saltar entre pantallas, ni salirse de la actividad principal sino sobreponen muy agilmente.

Este cariño a la hora de crear apps se puede extender de cualquier manera, es la creatividad del programador.

Las Apps se encuentran en el folder containers.

Cada vez que se quiera crear un app se debe:

1. Crear un folder nuevo en containers
2. Agregar el app al array de apps y al Menu en containers/index

Tipos de Apps Tradicionales

\*\* Table App
Apps sencillas y lineales de datos basadas en filas. Se visualizan en una tabla, se pueden crear, editar, borrar y ver.

\*\* Process App
Apps complejas que forman parte de procesos, como por ejemplo ordenes que deben ser creadas, aprobadas y facturadas.
Estas apps tienen la particularidad de contar con un campo estado que identifica su posicion en el proceso.

\*\* App Especial
Se pueden crear cualquier tipo de apps con todos los elementos del internet a su disposicion. Infograficos Interactivos, Mapas, incluso juegos. Un App
especial no necesita mas configuración ni es mas complicado crearlas que las tradicionales.

Componentes de las Apps Tradicionales
Las apps tradicionales tiene dos componentes importantes, las tablas y los forms. Ambos son altamente configurables y cuentan con la logica extendible para
adaptarse a todas las necesidades.

Tipos de Datos en las Apps Tradiciinales
Las componentes tradicionales pueden tener varios tipos de datos standard.

- string: campos de texto de hasta 255 caracteres
- boolean: campos binarios on/off
- number: campos numericos
- integer: campos numericos sin decimales
- select: seleccion individual de una lista
- multiSelect: opcion multiple
- autocomplete: seleccionar datos relacionados, por ejemplo el cliente de una orden.

Configuracion de Campos y Columnas
Todas las apps tradicionales estan basadas en filas y columnas, la configuracion de los campos y columnas realiza en el archivo container/APP_NAME/schema.json

schema.json

```
{
    "title":"App",
    "api":App",
    "path":"App",
    "properties":{
        "id":{},
        "name":{},
        "lastName":{
            "extends":"name",
            "title":"apellido",
        },
        "level":{
            "extends":"integer"
            "title":"Puntos",
        },
         "points":{
            "title":"Puntos",
            "render":"integer"
            "filter":"integer"
        }

    }
}
```

Las columnas se configuran segun su tipo en el campo properties. Como en el caso de id y name, se puede utilizar los mecanismos de ayuda del schema standard para evitar tener que duplicar codigo. De la misma forma lastName puede extender el campo standard name. Existen campos standard para muchos campos comunes.

Para mas informacion sobre la configuracion del archivo schema.json visite los docs docs/schema.md

Custom Comnponents
Todas las apps pueden tener componentes personalizados, para tipos de datos o funcionalidades adicionales. Por ejemplo los apps de recibos pueden tener un
componente que permite buscar y agregar el monto a pagar entre varias facturas. La creacion de estos componentes tampoco tiene restricciones y se configuran
dentro de el app especifico que las va utilizar.

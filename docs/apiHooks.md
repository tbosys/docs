Uso de datos externos

Hay tres formas de cargar datos desde un API y una forma de enviar cambios a un API, todas basadas en React Hooks.

Funcionalidades
Todos los hooks tienen un componente de loading y uno de error. El de error funciona con el componente <Error/> y el de loading con <SaveButton>. Algunos
Hooks tienen mas funcionalidades para filtrar y paging intelignete de datos.

useFetch
Es un hook que permite realizar un API call sencillo, cuenta con las funcionalidades basicas de un fetch hook como flags para loading y error.
Este hook no hace transformaciones y accede directamente el path del api sin realizar tranformaciones. Su manejo de errores es estandard

useQuery
Un hook que realizar un api call tipo query, incluye manejo de filtros y paging.

useProcessQuery
Un hook inteligente que mantiene el estado, es utilizado por el process app para poder sincronizar los cambios del entre filtros y estados en las app tradicionales.

useMutation
Hook que envia cambios al API, tiene control de carga, error y respuesta.

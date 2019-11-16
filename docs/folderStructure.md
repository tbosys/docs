La estructura de los archivos esta basada en componentes internos, los cuales solo deben ser reutilizados en su mismo nivel.La
import { Table } from '@material-ui/core/Table';

En el folder componentes estan todos los bloques que pueden ser reutilizados en las distintas apps. Incluso, un componente puede uttilizar otro componente.La

Cada componente puede tener componentes internos, estos componentes no puede ser utilizados por otros componentes.La

- componentes
  -SaveButton
  -components
  -spinner
  -label

  -Table
  -componentes
  -row
  -column
  -spinner
  -Form
  -componentes
  -Field
  -CustomButton

En este caso, el componte Table y el componente Form pueden utilizar el componente SaveButton.
Sin embargo ninguno puede utilzar los componentes internos de SaveButton como por ejemplo Spinner.
Por eso, table tiene sy propio spinner.

Los folders estructurales estan dividos de la siguiente forma

- business
  - hooks
  - schemas
- components -> Aqui es crean los componentes compartidos
- containers -> Aqui se crean las nuevas apps

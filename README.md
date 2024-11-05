## Enunciado del Ejercicio

**Objetivo:** Crear una aplicación en Vue.js que consuma la API de Dog CEO para mostrar imágenes de perros y permitir al usuario seleccionar diferentes razas.

## Instrucciones:

1. Configuración Inicial:

   - Configura un proyecto de Vue.js.
   - Instala Axios para realizar las solicitudes a la API.

2. Componentes:

   - Crea un componente llamado DogGallery que será el encargado de mostrar una galería de imágenes de perros.
   - Crea un componente llamado BreedSelector que contenga un `<select>` para elegir la raza de los perros.

3. Funcionalidad:

   - Usa Axios en el componente BreedSelector para hacer una solicitud a https://dog.ceo/api/breeds/list/all, lo cual te proporcionará la lista de razas disponibles.
   - Llena el `<select>` de BreedSelector con las razas obtenidas de la API.
     Cuando el usuario seleccione una raza, emite un evento hacia el componente DogGallery con la raza seleccionada.

4. Mostrar Imágenes:

   - En el componente DogGallery, escucha el evento emitido por BreedSelector.
   - Cuando se reciba una nueva raza, realiza una solicitud a https://dog.ceo/api/breed/{breed}/images/random/6 (reemplaza {breed} con la raza seleccionada) para obtener 6 imágenes aleatorias de perros de esa raza.
   - Muestra las imágenes en una galería.

5. Estilos y Diseño:

   - Aplica estilos CSS para organizar las imágenes en una cuadrícula de 3x2.
   - Muestra un mensaje de carga mientras se obtienen las imágenes de la API.

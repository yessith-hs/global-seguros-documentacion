# GlobalOnboardingComparadorCmp

### Descripción
- Muestra la lista de productos y gestionar la interacción del usuario con los detalles de los productos seleccionados.
- Calcula las comisiones globales basadas en valores seleccionados por el usuario de varios campos de lista de selección.
- Utiliza el modulo de **"uiObjectInfoApi"** el cual incluye adaptadores wire para obtener los metadatos del objeto Quote, asi como los valores de los campos de tipo picklist.
- Interactúa con un servicio llamado **gsvTvsCommissionCalculator** el cual es un Integration Procedure para el cálculo de comisiones.



### Atributos

| Atributo                        | Tipo    | Descripción                                                                                                                                                                                            |
|---------------------------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| listProducts                    | Array   | Lista de productos seleccionados por el usuario a partir de los datos ingresados previamente.                                                                                                          |
| loaded                          | Boolean | Indica si hay procesos en curso para manejar estados de carga.                                                                                                                                         |
| recommendedProducts             | Array   | Lista de productos recomendados que no están en la lista **listProducts** de los productos seleccionados                                                                                               |
| jsonData                        | Object  | JSON que contiene datos relevantes del flujo Omniscript.                                                                                                                                               |
| listOfQuoteDetails              | Array   | Contiene el listado de los detalles de las cotizaciones seleccionadas por el usuario, el cual se envia como parametro al componente **GlobalOnboardingQuoteCardCmp**.                                  |
| showNavigate                    | Boolean | Indica si se debe mostrar los botones de navegación dentro del slider de las tarjetas que muestran el detalle de las cotizaciones                                                                      |
| allProducts                     | Array   | Lista completa de productos obtenida desde la clase Apex **GlobalOnboardingGetAllProducts**.                                                                                                           |
| quote                           | Boolean | Variable que guarda el estado para mostrar en el front el boton de cotizar o el boton de crear oportunidad, esta variable es enviada como parametro al componente **GlobalOnboardingProductCardCmp**   |
| selectedProducts                | Array   | Productos seleccionados por el usuario.                                                                                                                                                                |
| dataLead                        | Object  | Información del lead extraída del JSON del Omniscript.                                                                                                                                                 |
| userProfile                     | String  | Perfil del usuario actual según datos en el JSON del Omniscript.                                                                                                                                       |

### Metodos

#### connectedCallback()
- Procesa datos iniciales desde omniJsonData.
- Convierte el objeto de los productos seleccionados en un array y los asigna a la variable **selectedProducts**.
- Obtiene la lista completa de productos mediante el llamado al metodo **getProducts()**
- Configura los colores y el dataset de los productos seleccionados mediante el llamado al metodo **setProductColorAndDataset()**.
- Genera la lista de productos recomendados mediante el llamado al metodo **getRecommendedProducts()**.
- Ordena la lista de productos seleccionados mediante el llamado al metodo **sortProductList()**.

#### getProducts()
- Obtiene la lista completa de productos mediante el método getAllProducst de la clase Apex **GlobalOnboardingGetAllProducts**.
- 
#### setProductColorAndDataset()
- Actualiza la lista de productos seleccionados con propiedades adicionales, como colores específicos y datos del lead.

#### getRecommendedProducts()
- Genera una lista de productos recomendados comparando la lista completa de productos con los seleccionados.

#### handleCreateOpp()
- Genera una oportunidad basada en un producto seleccionado.
- Actualiza las listas de productos recomendados y seleccionados.
- Muestra un mensaje en caso de error o éxito.

#### handleShowDetail()
- Muestra u oculta detalles de la cotización según la interacción del usuario.

#### deleteQuoteDetailCard()
- Recibe el Id de la cotización a eliminar de la vista de detalles de la cotización.

#### deleteRecommendedProducts()
- Recibe el codigo del producto a eliminar para luego filtra de la lista el productos a eliminar.

#### updateProductList()
- Agrega un producto a la lista seleccionada y actualiza sus propiedades visuales y de dataset.

#### Dependencias

- Apex: GlobalOnboardingGetAllProducts

#### Módulos Locales:
- Remote: Clase auxiliar para manejar acciones remotas.
- util: Funciones utilitarias, incluyendo:

 getDiffProductLists

 sortProductList

 NAME_SERVICE

 convertToArray

#### Salesforce Lightning:
- ShowToastEvent: Utilizado para mostrar mensajes de éxito o error al usuario.


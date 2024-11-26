# GlobalOnboardingProductCardCmp
- componente es un hijo de GlobalOnboardingComparadorCmp y se utiliza para mostrar una tarjeta de producto individual con sus detalles, funcionalidades de navegación, creación de oportunidades y vista previa de archivos adjuntos.

### Atributos

| Atributo                      | Tipo            | Descripción                                                                                                                                                                                              |
|-------------------------------|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| productDetail                 | Object          | Contiene los detalles del producto mostrado en la tarjeta.                                                                                                                                               |
| quote                         | Boolean         | Variable que guarda el estado para mostrar en el front el boton de cotizar o el boton de crear oportunidad, esta variable es enviada como parametro al componente **GlobalOnboardingProductCardCmp**     |
| userProfile                   | String          | Perfil del usuario actual según datos en el JSON del Omniscript.                                                                                                                                         |
| communityUserProfile          | String          | Perfil por defecto de usuario de la comunidad para validaciones específicas.                                                                                                                             |
| jsonData                      | Object          | JSON que contiene datos relevantes del flujo Omniscript.                                                                                                                                                 |
| DEFAULT_PRODUCT_ICON          | String          | URL del icono predeterminado para productos.                                                                                                                                                             |
| PRODUCT_CARD_UI               | Object          | Configuración de las tarjetas de productos según el código del producto.                                                                                                                                 |

### Getters

#### productIcon
- Retorna la URL del icono asociado al producto según su código. Si no existe, usa el icono predeterminado **DEFAULT_PRODUCT_ICON**.

#### productBorderColor
- Retorna el estilo CSS para definir el borde de la tarjeta el cual se obtiene del objeto **productDetail**.

#### productDataSetName
- Retorna el nombre del conjunto de datos asociado al producto según la configuración de PRODUCT_CARD_UI.

### Metodos

#### handleNavigate()
Navega a un destino específico basado en la configuración del producto.
- Si el usuario pertenece a la comunidad, se redirige a una página web específica; de lo contrario, se navega a un componente LWC con parámetros personalizados.
- Utiliza **[NavigationMixin](https://developer.salesforce.com/docs/platform/lwc/guide/use-navigate-basic.html)** para manejar la navegación.


#### handleCreateOpp()
- Dispara un evento personalizado **createopp** con los detalles del producto para crear una oportunidad.


#### handleShowQuoteDetail()
- Dispara un evento personalizado **showdetail** para mostrar o eliminar detalles de cotización según la interacción del usuario.

#### previewHandler()
- Gestiona la vista previa de archivos adjuntos asociados a una cotización.
- Utiliza NavigationMixin para redirigir al previsualizador de archivos.
- Acciones:
1. Obtiene el archivo adjunto usando fetchAttachment.
2. Navega a la página de previsualización de archivos si se encuentra un documento.
Eventos Relacionados:


#### fetchAttachment()
- Obtiene el primer archivo adjunto asociado a una cotización mediante la llamada al metodo **getAttachments** de la calse Apex **OnboardingAttachmentController**.



#### Dependencias

- Apex:
getAttachments: Recupera archivos adjuntos relacionados con una cotización.

- Salesforce Lightning:
NavigationMixin: Para navegación personalizada en Salesforce.

- Recursos Estáticos:
Iconos personalizados para productos.



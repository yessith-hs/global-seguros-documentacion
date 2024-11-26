# GlobalOnboardingQuoteCardCmp
- componente es un hijo de **GlobalOnboardingComparadorCmp** y se utiliza para manejar la visualización y navegación de las tarjetas de detalle de la cotización

### Atributos

| Atributo                                  | Tipo    | Descripción                                                                                                                                                                                                |
|-------------------------------------------|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| quoteDetail                               | Object  | Recibe los detalles del producto de la cotización.                                                                                                                                                         |
| loaded                                    | Boolean | Indica el estado de carga del componente.                                                                                                                                                                  |
| renderFooter                              | Boolean | Controla si se debe mostrar el pie de página.                                                                                                                                                              |
| topImputList                              | Array   | Contiene los campos que se mostrarán en la sección superior de la tarjeta.                                                                                                                                 |
| bottomImputList                           | Array   | Contiene los campos que se mostrarán en la sección inferior de la tarjeta.                                                                                                                                 |
| dateOfQuote                               | String  | Indica la fecha de creación de la cotización                                                                                                                                                               |
| validityOfQuote                           | String  | Fecha de vencimiento de la cotización.                                                                                                                                                                     |
| productDescription                        | String  | Descripción del producto cotizado.                                                                                                                                                                         |
| DEFAULT_PRODUCT_ICON                      | String  | Icono predeterminado para productos sin una configuración específica.                                                                                                                                      |


### Configuraciones del Producto
El objeto **quoteDetailsUI** contiene la configuración de los productos disponibles y se compone de la siguente manera:

- render: indica si el producto debe mostrarse.
- footerRender: controla si se debe mostrar el pie de página.
- name: nombre del producto.
- topImputList y bottomImputList: especifican los campos a mostrar en la tarjeta.
- icon: define el icono asociado al producto.
- target: referencia al omniscript objetivo para navegación.
- tabLabel: etiqueta de la pestaña que se abre al navegar.
- dataSet: conjunto de datos asociado al producto.

### Ejemplo de configuración:
```js
"69_1_1": {
    render: false,
    footerRender: false,
    name: "Global Universidad Garantizada Semestres",
    topImputList: [
        { label: "Solución", field: "ProductoSeleccionadoEducativo__c" },
        { label: "Año estimado de ingreso a la universidad", field: "AnioMaduracion__c" },
        { label: "Cobertura máxima de semestres", field: "Total__c" },
        { label: "Valor de la prima", field: "Aporte_Unico_Inicial__c" }
    ],
    bottomImputList: [],
    icon: EDUCATIVO_ICON,
    target: "c:gsvTvsPerfiladorEducativoEnglish",
    tabLabel: "gsvTvs_PerfiladorEducativo",
    dataSet: "Educativo"
}

```
### Getters

#### productName()
Devuelve el nombre del producto según el código (productCode) recibido.

#### productRender()
Verifica si el producto debe renderizarse en la tarjeta.

#### footerRender()
Determina si se muestra el pie de página de acuerdo con la configuración del producto.

#### productIcon()
Retorna el icono del producto según su configuración, o el icono predeterminado si no está definido.

#### productDataSetName()
Devuelve el nombre del conjunto de datos asociado al producto.

### Metodos

#### @wire wiredQuote
Se conecta al registro de la cotización usando el metodo **[getRecord](https://developer.salesforce.com/docs/platform/lwc/guide/reference-wire-adapters-record.html)**. Extrae los valores de los campos definidos en FIELDS y los asigna al componente.

#### setDataQuote(quote)
Procesa los datos de la cotización y los asigna a las propiedades topImputList, bottomImputList, dateOfQuote, y validityOfQuote.

#### navigateToQuoteRecord(event)
Navega al registro de la cotización en Salesforce.

#### handleNavigate(event)
Navega a un componente específico (definido en el atributo target) con parámetros personalizados.

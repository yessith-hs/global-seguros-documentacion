# GlobalOnboardingProgressIndicatorCmp
actúa como un indicador de progreso dinámico dentro del flujo de onboarding global. Este componente utiliza configuraciones específicas basadas en el producto seleccionado para personalizar el diseño y la navegación, brindando una experiencia visual adaptada.

### Dependencias

- OmniscriptBaseMixin: Permite la integración con OmniScripts.
- getAllProducst: Método de la clase Apex **GlobalOnboardingGetAllProducts** para obtener la lista de productos disponibles.

### Atributos

| Atributo                                      | Tipo        | Descripción                                                                                       |
|-----------------------------------------------|-------------|---------------------------------------------------------------------------------------------------|
| productcode                                   | String      | Código del producto que define la configuración del componente. Proporcionado desde el exterior.  |
| percentageValue                               | String      | Representa el porcentaje actual del progreso.                                                     |
| currentStep                                   | String      | Paso actual del flujo.                                                                            |
| products                                      | Array       | Lista de productos obtenida desde la clase Apex **GlobalOnboardingGetAllProducts**                |
| steps                                         | Array       | Pasos dinámicos cargados desde omniJsonData para indicar en que paso se encuentra el usuario.     |
| progressStep                                  | Array       | Array con la configuración de los pasos a mostrar en el html                                      |
| title                                         | String      | Título dinámico basado en el producto seleccionado.                                               |
| totalSteps                                    | String      | Número total de pasos para el producto actual.                                                    |

### Constantes

- DEFAULT_TITLE: "Descubre Tu Póliza Ideal".
- DEFAULT_STEPS: Número de pasos predeterminados, 4.
- DEFAULT_GRAADIENT_COLOR: Color de gradiente predeterminado, "#00327D".
- DEFAULT_BACKGROUND_IMAGE: Imagen de fondo predeterminada.
- PRODUCT_BACKGROUND_STYLE: Configura los estilos específicos de cada producto segun el codigo del producto:

```js
{
  "60_3":{
    background: Imagen de fondo personalizada.
    gradientColor: Color de gradiente.  
  }
}
```

### Getters

- backgroundImage
Retorna el estilo CSS dinámico para la imagen de fondo, dependiendo del producto seleccionado o el estilo predeterminado.

- backgroundStyle
Retorna el estilo CSS del gradiente dinámico para el fondo del componente.

### Métodos

#### connectedCallback()
- Llama al método **getProducts()** para cargar los productos.
- Invoca **setCurrentStepAndPercentage()** para determinar el progreso actual.
- Configura los detalles del producto mediante **getProductDetail()**.

#### getProducts()
- Método asíncrono que realiza una llamada a la clase Apex **GlobalOnboardingGetAllProducts**para obtener todos los productos.

#### getProductDetail()
- Configura los detalles del producto seleccionado:
- Determina el número total de pasos (totalSteps).
- Configura los pasos (progressStep) y el título (title) en base al producto actual.
- Si no se especifica un producto, utiliza los valores predeterminados.

#### setCurrentStepAndPercentage()
- Determina el paso actual y el porcentaje de progreso utilizando los datos de omniJsonData.
- Asigna los valores a las propiedades steps, percentageValue y currentStep.

#### createStepsArray(steps)

Crea un array dinámico con la configuración de los pasos basados en el número total de pasos.
Cada paso incluye:
- id: Identificador único.
- label: Etiqueta descriptiva.
- value: Valor asociado al paso.

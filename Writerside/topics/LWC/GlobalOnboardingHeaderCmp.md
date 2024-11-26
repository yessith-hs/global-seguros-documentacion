# GlobalOnboardingHeaderCmp
gestionar el encabezado de un flujo de onboarding. Integra navegación personalizada y utiliza configuraciones de OmniScript para interactuar dinámicamente con otras partes de la aplicación. 

### Atributos

| Atributo                            | Tipo        | Descripción                                                                                                                                                                                                                           |
|-------------------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| communityUserProfile                | String      | Define el perfil por defecto para usuarios comunitarios.                                                                                                                                                                              |
| logo                                | String      | Ruta del logo del encabezado, cargado desde un recurso estático.                                                                                                                                                                      |
| dataLead                            | String      | ID del lead utilizado en el flujo de onboarding.                                                                                                                                                                                      |
| userProfile                         | String      | Perfil del usuario actual según datos en el JSON del Omniscript.                                                                                                                                                                      |
| dataHeader                          | Array       | Contiene información del encabezado, obtenida dinámicamente desde el objeto omniJsonData.                                                                                                                                             |
| dataOmniscript                      | Object      | Define las configuraciones de navegación para diferentes pasos del flujo de onboarding.                                                                                                                                               |


### Configuraciones de los steps
El objeto **quoteDetailsUI** contiene la configuración de navegación para diferentes pasos del flujo y se compone de la siguente manera:

- target: Componente objetivo.
- tabLabel: Etiqueta de la pestaña.
- namedPage: Nombre de la página utilizada para navegación en comunidades.

### Ejemplo de configuración:
```js
   Perfilamiento: {
      target: "c:gsvFormularyEnglish",
      tabLabel: "gsvFormulary",
      namedPage: "onboarding"
    },

```

### Métodos

#### connectedCallback()
- Asigna datos dinámicos desde omniJsonData a las propiedades dataHeader, dataLead y userProfile.

#### handleNavigate(event)
- Método para manejar la navegación cuando un usuario selecciona un paso del flujo.
- Verifica si el paso está completo mediante la clase **isCompleted** en el elemento HTML.
- Obtiene la configuración del paso desde **dataOmniscript** y llama al método **navigateToOmniscript()**.

#### navigateToOmniscript(omniData)
- Método de navegación basado en la configuración de OmniScript.
- Si el usuario pertenece a un perfil comunitario, redirige a una página web (standard__webPage).
De lo contrario, navega a un componente de OmniScript (vlocityLWCOmniWrapper) con parámetros personalizados como:
```js 
{
  c__target: Componente objetivo.
  c__layout: Layout de Lightning.
  c__tabIcon: Icono de la pestaña.
  c__tabLabel: Etiqueta de la pestaña.
  c__DataLeadId: ID del lead.
}
```
#### activeMenu()
- Activa o desactiva el menú lateral en la interfaz.
- Alterna las clases CSS active y cross en los elementos correspondientes.

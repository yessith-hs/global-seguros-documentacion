# Artefactos Utilizados

La arquitectura definida para los procesos del flujo de **Global Onboarding** utilizan los siguientes artefactos de Salesforce Vlocity

# OmniScript

| Nombre                           | Descripción                                                                                |
|----------------------------------|--------------------------------------------------------------------------------------------|
| gsvFormulary                     | Gestiona el flujo principal por el que se inicia el proceso de Onboarding                  |
| gsvDatacomparador                |                                                                                            |
| gsvTvs_PerfiladorProductos       |                                                                                            |
| gsvTvs_PerfiladorPension         | Formulario en el que se gestiona el proceso de perfilamiento para el producto de Pension   |
| gsvTvs_PerfiladorRenta           | Formulario en el que se gestiona el proceso de perfilamiento para el producto de Renta     |
| gsvTvs_PerfiladorVida            | Formulario en el que se gestiona el proceso de perfilamiento para el producto de Vida      |
| gsvTvs_PerfiladorIndx            | Formulario en el que se gestiona el proceso de perfilamiento para el producto de Indx      |
| gsvTvs_PerfiladorEducativo       | Formulario en el que se gestiona el proceso de perfilamiento para el producto de Educativo |
| gsvTvs_PerfiladorEduFlex         | Formulario en el que se gestiona el proceso de perfilamiento para el producto de Eduflex   |
| gsvTvsFormularioSeguroEducativo  |                                                                                            |
| gsvTvsFormularioSolicitudCredito | Formulario en el que se gestiona el proceso de solicitud de credito                        |
| gsvTvsOnboPagos                  |                                                                                            |



# DataRaptors

| Nombre del artefacto                                         | Descripción |
|--------------------------------------------------------------|-------------|
| gsvTvsExtractDataComparador                                  |             |
| gsvtvsOnbUpdateQuote                                         |             |
| gsvTvsGetProductActive                                       |             |

## Integration Procedures

| Nombre del Integration Procedure | Descripción                                                                   |
|----------------------------------|-------------------------------------------------------------------------------|
| createOppEducativo               | Gestiona el proceso de creación de una oportunidad para el producto Educativo |
| createOppEduFlex                 | Gestiona el proceso de creación de una oportunidad para el producto Edu Flex  |
| createOppIndx                    | Gestiona el proceso de creación de una oportunidad para el producto Indx      |
| createOppPension                 | Gestiona el proceso de creación de una oportunidad para el producto Pension   |
| createOppRenta                   | Gestiona el proceso de creación de una oportunidad para el producto Renta     |
| createOppVida                    | Gestiona el proceso de creación de una oportunidad para el producto Vida      |
|                                  |                                                                               |
|                                  |                                                                               |
|                                  |                                                                               |
|                                  |                                                                               |



## Custom Metadata type

| Name                                 | Fields Name                                                                                       | Descripción                                                                          |
|--------------------------------------|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| globalOnboardingProductList          | productCode__c, productColor__c, productName__c,productDescription__c,productSteps__c,isActive__c | Gestiona los producto a mostrar y filtrar por los componentes LWC                    |


## Apex Classes

| Nombre de Clase                  | Descripción                                                                                                                                              |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| GlobalOnboardingGetAllProducts   | recuperar la lista de productos configurados en un tipo de metadatos personalizados llamado **globalOnboardingProductList__mdt**                         |
| OnboardingAttachmentController   | gestionar y recuperar los adjuntos asociados a un registro en Salesforce. Específicamente, permite obtener el último adjunto relacionado con un registro |


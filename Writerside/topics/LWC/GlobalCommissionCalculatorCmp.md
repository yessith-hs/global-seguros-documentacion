# GlobalCommissionCalculatorCmp

### Descripción
- Calcula las comisiones globales basadas en valores seleccionados por el usuario de varios campos de lista de selección.
- Utiliza el modulo de **"uiObjectInfoApi"** el cual incluye adaptadores wire para obtener los metadatos del objeto Quote, asi como los valores de los campos de tipo picklist.
- Interactúa con un servicio llamado **gsvTvsCommissionCalculator** el cual es un Integration Procedure para el cálculo de comisiones.

### Dependencias
- `globalCommissionCalculatorCmpRemote`

### Atributos

| Atributo                | Tipo     | Descripción                                                                 |
|-------------------------|----------|-----------------------------------------------------------------------------|
| comisionBruta           | @track   | Contiene el valor calculado de la comisión.                                 |
| quoteRecordTypeId       | String   | ID del RecordType para el objeto Quote.                                     |
| quoteProduct            | Array    | Contiene los valores del picklist **ProductoSeleccionadoEducativo__c**      |
| quoteCoverageLimit      | Array    | Contiene los valores del picklist **Limite_coberturas__c**                  |
| quoteNumSemester        | Array    | Contiene los valores del picklist **Cantidad_de_semestres__c**              |
| quotePremiumPeriodicity | Array    | Contiene los valores del picklist **Periodicidad_de_la_prima_de_ahorro__c** |
| quotePremiumPayment     | Array    | Contiene los valores del picklist **yearPay__c**                            |

### Metodos

#### connectedCallback()
- Inicializa la instancia Remote para la invocación del servicio **gsvTvsCommissionCalculator**.

#### handleSelect()
- Captura los valores selecionados por el usuario en los campos de tipo lista para prepara payload que sera enviado al servicio **gsvTvsCommissionCalculator**.

#### calcularComisiones()
- Envía el payload hacia el servicio **gsvTvsCommissionCalculator** el cual es un Integration Procedure, para el cálculo de comisiones.
- Actualiza la variable de **comisionBruta** con la respuesta del servicio.

### Wired Metodos

#### getObjectInfo
- Recupera el ID del record type para el objeto Quote

#### productFieldPicklistResults({ error, data })
- Recupera los valores de la lista de selección para el campo ProductoSeleccionadoEducativo__c

#### coverageFieldPicklistResults({ error, data }) 
- Recupera los valores de la lista de selección para el campo Limite_coberturas__c

#### semesterFieldPicklistResults({ error, data }) 
- Recupera los valores de la lista de selección para el campo Cantidad_de_semestres__c

#### periodicityFieldPicklistResults({ error, data }) 
-Recupera los valores de la lista de selección para el campo Periodicidad_de_la_prima_de_ahorro__c 

#### paymentFieldPicklistResults({ error, data }) 
- Recupera los valores de la lista de selección para el campo yearPay__c
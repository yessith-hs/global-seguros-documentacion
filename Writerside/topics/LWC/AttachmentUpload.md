# AttachmentUpload

### Descripción
- Realiza el cargue de documentos a la plataforma de Salesforce mediante el uso del componente nativo [**File Upload** ](https://developer.salesforce.com/docs/component-library/bundle/lightning-file-upload/documentation)
### Dependencias
- `globalCommissionCalculatorCmpRemote`

### Atributos

| Atributo                | Tipo     | Descripción                                                                                                       |
|-------------------------|----------|-------------------------------------------------------------------------------------------------------------------|
| recordId                | @api     | Id del record en el cual van a estar asociados los documentos a cargar                                            |
| fileName                | String   | Nombre del tipo de documento que se muestra cuando el documento se carga con exito                                |
| Documents               | Array    | Contiene los tipos de documentos que el usuario tiene que cargar al sistema y estos se muestran luego en el front |
                                                              |

### Metodos

#### uploadedFile()
- Obtiene el nombre del tipo de documento a cargar, el cual es mostrado en una ventana emergente cuado este es cargado con exito.
- Realiza el llamado al metodo handleUploadFinished()

#### handleUploadFinished()
- Metodo que se ejecuta una vez el documento fue cargado con exito
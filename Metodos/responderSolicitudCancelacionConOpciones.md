

# responderSolicitudCancelacionConOpciones


El método *responderSolicitudCancelacionConOpciones* permite responder las peticiones de cancelación realizadas al contribuyente como receptor de Comprobantes Fiscales Digitales por Internet (CFDI).


## Request


```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:responderSolicitudCancelacionConOpciones>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <rfcReceptor>?</rfcReceptor>
         <!--Zero or more repetitions:-->
         <arregloUUID>?</arregloUUID>
         <cert>cid:227727865817</cert>
         <key>cid:131179918080</key>
         <keyPass>?</keyPass>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:responderSolicitudCancelacionConOpciones>
   </soapenv:Body>
</soapenv:Envelope>
```

### Parámetros

| Atributo      | Requerido | Tipo     | Descripción |
| ------------- |:--------- |:-------- |:----------- |
| contrato      | Si        | String   | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | String   | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | String   | Contraseña del usuario con el que se autenticará en el servicio. |
| rfcReceptor   | Si        | String   | RFC del contribuyente del que responde las peticiones de cancelación que tiene como receptor de los CFDI.
| arregloUUID   | Si        | String[] | UUID y respuesta a la peticipión (`Aceptación` o `Rechazo`), separada por el carácter pipe (\|). **Ejemplo**: `UUID|Aceptacion` `UUID|Rechazo` |
| cert          | Si        | byte[]   | Certificado de Sello Digital (CSD). |
| key           | Si        | byte[]   | Llave privada del CSD. |
| keyPass       | Si        | String   | Contraseña de la llave privada del CSD. |
| opciones      | Opcional  | String[] | Opciones para el servicio. |



## Response

```xml
  <servicioAceptacionRechazo>
    <procesoOk/>
    <codigo/>
    <codigoEstatus/>
    <rfcReceptor/>
    <rfcPac/>
    <fecha/>
    <mensaje/>
    <fecha/>
    <folios>
      <Folio>
        <uuid/>
        <estatusUuid/>
        <respuesta/>
      <Folio/>
    </Folios>
</servicioAceptacionRechazo>
```


### `<servicioAceptacionRechazo/>`

| Atributo      | Tipo     | Descripción |
| ------------- |:-------- |:----------- |
| procesoOk     | boolean  | Indica si la invocación del método fue concluida exitosamente. |
| codigo        | String   | El código del servicio de consulta. [Códigos del servicio](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigos.md) |
| codigoEstatus | String   | Descripción del código. |
| rfcReceptor   | String   | String   | RFC del contribuyente que responde las peticiones de cancelación como receptor de los CFDI. |
| rfcPac        | String   | RFC del Proveedor Autorizado de Certificación (PAC) que realizó la cancelación.
| fecha         | String   | Fecha en la que se responde la petición. |
| Folios        | Folio[]  | Nodo que expresa los folios. |


### `<Folio/>`

| Atributo    | Tipo   | Descripción |
| ----------- |:------ |:----------- |
| uuid        | String | Folio fiscal del CFDI que se procesa. |
| EstatusUuid | String | Estatus del CFDI que procesa ante el SAT. |
| respuesta   | String | Respuesta por parte del SAT. |



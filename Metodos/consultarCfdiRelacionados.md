# consultarCfdiRelacionados

El método *consultarCfdiRelacionados* recibe el UUID (Folio fiscal) de un Comprobante Fiscal Digital por Internet (CFDI), retorna los datos de los documentos relacionados.


## Request

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:consultarCfdiRelacionados>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <rfcReceptor>?</rfcReceptor>
         <uuid>?</uuid>
         <cert>cid:830565485722</cert>
         <key>cid:1056772432149</key>
         <keyPass>?</keyPass>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:consultarCfdiRelacionados>
   </soapenv:Body>
</soapenv:Envelope>
```

### Parámetros

| Atributo      | Requerido | Tipo     | Descripción |
| ------------- |:--------- |:-------- |:----------- |
| contrato      | Si        | String   | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | String   | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | String   | Contraseña del usuario con el que se autenticará en el servicio. |
| rfcReceptor   | Si        | String   | RFC del receptor del CFDI a consultar. |
| uuid.         | Si        | String   | Folio fiscal del CFDI a consultar. |
| cert          | Si        | byte[]   | Certificado de Sello Digital (CSD). |
| key           | Si        | byte[]   | Llave privada del CSD. |
| keyPass       | Si        | String   | Contraseña de la llave privada del CSD. |
| opciones      | Si        | String[] | Opciones para el servicio. |


## Response

```xml 
 <servicioConsultaRelacionados>
	<consultaOk/>
	<UuidConsultado/>
	<codigo/>
	<mensaje/>
	<resultado/>
	<UuidsRelacionadosPadre>
		<UuidPadre>
			<Uuid/>
			<RfcEmisor/>
			<RfcReceptor/>
		</UuidPadre>
	</UuidsRelacionadosPadre>
	<UuidsRelacionadosHijos>
		<UuidRelacionado>
			<Uuid/>
			<RfcEmisor/>
			<RfcReceptor/>
		</UuidRelacionado>
	</UuidsRelacionadosHijos>
	</servicioConsultaRelacionados>
```

### `<servicioConsultaRelacionados/>`

| Atributo               | Tipo          | Descripción |
| ---------------------- |:------------- |:----------- |
| consultaOk             | boolean       | Indica si la invocación del método fue concluida exitosamente. |
| UuidConsultado         | String	 | Contrato de Pade Timbrado Fiscal enviado por el usuario (informativo). |
| codigo                 | String        | Código de respuesta del servicio del SAT. |
| mensaje                | String        | Mensaje del servicio del SAT, se retorna en caso de ocurrir un error. |
| resultado              | String        | Resultado de la consulta realizada por el servicio del SAT. |
| UuidsRelacionadosPadre | UuidPadre[]       | Nodo que expresa los datos de los CFDI que tienen relacionados el CFDI consultado en su nodo cfdiRelacionados(CFDI Padre). |
| UuidsRelacionadosHijos | UuidRelacionado[] | Nodo que expresa los datos de los CFDI que tiene el CFDI consultado en su nodo cfdiRelacionados(CFDI hijo).

### `<UuidPadre/>`

| Atributo    | Tipo   | Descripción |
| ----------- |:------ |:----------- |
| Uuid        | String | Folio fiscal del CFDI. |      
| RfcEmisor   | String | RFC emisor del CFDI. | 
| RfcReceptor | String | RFC receptor del CFDI. | 

### `<UuidRelacionado/>`

| Atributo    | Tipo   | Descripción |
| ----------- |:------ |:----------- |
| Uuid        | String | Folio fiscal del CFDI. | 
| RfcEmisor   | String | RFC emisor del CFDI. |
| RfcReceptor | String | RFC receptor del CFDI. |



# timbradoDoc

## SOAP

* [acuseCancelacion](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/Metodos/Acuse%20Cancelaci%C3%B3n.md)
* [cancelar](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/Metodos/cancelar.md)
* [cancelarConOpciones](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/Metodos/cancelarConOpciones.md)
* [cfdiPorUUID](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/Metodos/cfdiPorUUID.md)
* [consultarCfdiRelacionados](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/Metodos/consultarCfdiRelacionados.md)

### Content Type 

Todas los requests deben contener un encabezado HTTP `Content-Type: text/xml; charset=utf-8`.


## consultarEstatusComprobante

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:consultarEstatusComprobante>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <!--Optional:-->
         <uuid>?</uuid>
         <!--Optional:-->
         <rfcEmisor>?</rfcEmisor>
         <!--Optional:-->
         <rfcReceptor>?</rfcReceptor>
         <!--Optional:-->
         <total>?</total>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:consultarEstatusComprobante>
   </soapenv:Body>
</soapenv:Envelope>
```

| Atributo      | Requerido | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | Si        | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | Contraseña del usuario con el que se autenticará en el servicio. |
| uuid          | Si       |              |
| rfcEmisor     | Si       |              |
| rfcReceptor   | Si       |              |
| total         | Si       |              |
| opciones      | Si       |              |


## consultarPeticionesPendientes

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:consultarPeticionesPendientes>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <!--Optional:-->
         <rfcReceptor>?</rfcReceptor>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:consultarPeticionesPendientes>
   </soapenv:Body>
</soapenv:Envelope>
```

| Atributo      | Requerido | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | Si        | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | Contraseña del usuario con el que se autenticará en el servicio. |
| rfcReceptor   | Si       |              |
| opciones      | Si       |              |

## responderSolicitudCancelacionConOpciones

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:responderSolicitudCancelacionConOpciones>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <!--Optional:-->
         <rfcReceptor>?</rfcReceptor>
         <!--Zero or more repetitions:-->
         <arregloUUID>?</arregloUUID>
         <!--Optional:-->
         <cert>cid:227727865817</cert>
         <!--Optional:-->
         <key>cid:131179918080</key>
         <!--Optional:-->
         <keyPass>?</keyPass>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:responderSolicitudCancelacionConOpciones>
   </soapenv:Body>
</soapenv:Envelope>
```

| Atributo      | Requerido | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | Si        | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | Contraseña del usuario con el que se autenticará en el servicio. |
| rfcReceptor   | Si       |              |
| arregloUUID   | Si       |              |
| cert          | Si       |              |
| key           | Si       |              |
| keyPass       | Si       |              |
| opciones      | Si       |              |

## timbrado

Parámetro

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:timbrado>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <!--Optional:-->
         <cfdiXml>?</cfdiXml>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:timbrado>
   </soapenv:Body>
</soapenv:Envelope>
```

| Atributo      | Requerido | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | Si        | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | Contraseña del usuario con el que se autenticará en el servicio. |
| cfdiXml       | Si       |              |
| opciones      | Si       |              |

### Response 
```xml
<servicioTimbrado>
	<id/>
	<timbradoOk/>
	<contrato/>
	<codigo/>
	<mensaje/>
	<version/>
	<uuid/>
	<FechaTimbrado/>
	<selloCFD/>
	<noCertificadoSAT/>
	<selloSAT/>
	<xmlBase64/>
	<pdfBase64/>
	<saldo/>
</servicioTimbrado>
```

### Opciones del servicio

* CALCULAR_SELLO
* CONSULTAR_SALDO
* ENVIAR_AMBOS:
* ADDENDA:LIBRE:
* REGRESAR_CON_ERROR_307_XML
* OBSERVACIONES:
* REGRESAR_CADENA_ORIGINAL
* GENERAR_PDF

## timbradoBase64

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:timbradoBase64>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <!--Optional:-->
         <cfdiXmlBase64>?</cfdiXmlBase64>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:timbradoBase64>
   </soapenv:Body>
</soapenv:Envelope>
```

| Atributo      | Requerido | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | Si        | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | Contraseña del usuario con el que se autenticará en el servicio. |
| cfdiXmlBase64 | Si       |              |
| opciones      | Si       |              |

## timbradoBase64Prueba

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:timbradoBase64Prueba>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <!--Optional:-->
         <cfdiXmlBase64>?</cfdiXmlBase64>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:timbradoBase64Prueba>
   </soapenv:Body>
</soapenv:Envelope>
```

| Atributo      | Requerido | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | Si        | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | Contraseña del usuario con el que se autenticará en el servicio. |
| cfdiXmlBase64 | Si       |              |
| opciones      | Si       |              |

## timbradoPrueba
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:timbradoPrueba>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <!--Optional:-->
         <cfdiXml>?</cfdiXml>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:timbradoPrueba>
   </soapenv:Body>
</soapenv:Envelope>
```

| Atributo      | Requerido | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | Si        | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | Contraseña del usuario con el que se autenticará en el servicio. |
| cfdiXml       | Si       |              |
| opciones      | Si       |              |




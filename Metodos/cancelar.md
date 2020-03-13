# Método: cancelar

El método *cancelar* crea una solicitud de cancelación para uno o más Comprobantes Fiscales Digitales por Internet (CFDI).

El 1 de noviembre del 2018 los servicios de cancelación se actualizaron. Las facturas en algunos casos, solo podrán cancelarse cuando el receptor de la factura acepte dicha cancelación. Te recomendamos consultar el nuevo esquema de cancelación.

## Request

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:cancelar>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <rfcEmisor>?</rfcEmisor>
         <!--Zero or more repetitions:-->
         <arregloUUID>?</arregloUUID>
         <cert>cid:175473078103</cert>
         <key>cid:217884016038</key>
         <keyPass>?</keyPass>
      </tim:cancelar>
   </soapenv:Body>
</soapenv:Envelope>
```

### Parámetros

| Atributo      | Requerido | Tipo      | Descripción |
| ------------- |:--------- |:--------- |:----------- |
| contrato      | Si        | String | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | String | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | String | Contraseña del usuario con el que se autenticará en el servicio. |
| rfcEmisor     | Si        | String | RFC del emisor al que pertenecen los CFDI a cancelar. |
| arregloUUID   | Si        |String[] | UUID, RFC Receptor, RFC Emisor y Total del CFDI a cancelar, separada por el carácter pipe (\|). **Ejemplo**: <arregloUUID>UUID\|RFC_Receptor\|RFC_Emisor\|Total</arregloUUID> |
| cert          | Si        | byte[] | Certificado de Sello Digital (CSD). Debe ser el mismo con el que se genero el sello digital de los CFDI a cancelar.         |
| key           | Si        | byte[] | Llave privada del CSD. |
| keyPass       | Si        | String | Contraseña de la llave privada del CSD. |


## Response

```xml
<servicioCancel>
	<statusOk/>
	<rfc/>
	<codigo/>
	<procesados/>
	<cancelados/>
	<mensaje/>
	<cancelaciones>
		<cancelacion>
			<uuid/>
			<codigo/>
			<mensaje/>
		</cancelacion>
	</cancelaciones>
	<acuseCancelBase64/>
</servicioCancel>
```

### servicioCancel

| Atributo      | Tipo          | Descripción |
| ------------- |:------------- |:----------- |
| statusOk      | boolean       | Indica si la invocación del método fue concluida exitosamente. |
| rfc           | string        | El RFC del emisor enviado por el usuario (informativo). |
| codigo        | string        | El código del servicio de consulta. [Códigos del servicio](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigos.md)
| procesados    | int           | Indica el número de CFDI que fueron procesados para su cancelación. |
| cancelados    | int           | Indica el numero de CFDI que posterior a su procesamientos, fueron efectivamente cancelados. |
| mensaje       | string        | En caso de que haya un error, se devolverá la descripción del mismo. |
| cancelaciones | Cancelacion[] | Nodo que expresa las cancelaciones. |
| xmlBase64     | string        | XML del acuse de cancelación del SAT, códificado en base64. |

### cancelacion
| Atributo      | Tipo          | Descripción |
| ------------- |:------------- |:----------- |
| uuid          | string        | UUID del CFDI procesado. | https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigosCancelacion.md
| codigo        | string        | El código del servicio de cancelación. [Códigos de cancelación](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigosCancelacion.md)
| mensaje       | string        | En caso de que haya un error, se devolverá la descripción del mismo. |

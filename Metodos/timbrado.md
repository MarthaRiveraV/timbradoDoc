# timbrado

El método *timbrado* recibe el XML de un Comprobante Fiscal Digital por Internet (CFDI) a timbrar, valida su estructura y retorna el XML del CFDI con el complemento de Timbre Fiscal Digital.


## Request


```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:timbrado>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <cfdiXml>?</cfdiXml>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:timbrado>
   </soapenv:Body>
</soapenv:Envelope>
```

### Parámetros

| Atributo      | Requerido | Tipo     | Descripción |
| ------------- |:--------- |:-------- |:----------- |
| contrato      | Si        | String   | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | String   | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | String   | Contraseña del usuario con el que se autenticará en el servicio. |
| cfdiXml       | Si        | String   | XML del CFDI a timbrar en texto plano. |
| opciones      | Si        | String[] | Opciones para el servicio. | 


### Opciones

#### ADDENDA:LIBRE
Esta opción recibe el XML de la addenda códificado en base 64, el cual sera anexado al CFDI posterior a su timbrado.

**Formato**
ADDENDA:LIBRE:addenda_base64

**Observaciones**
* La validación de la addenda en contenido y estructura es responsabilidad del usuario.
* La addenda será anexada al CFDI en el nodo **<cfdi:Addenda>**.

#### CALCULAR_SELLO
Esta opción indica que se debe calcular el sello del CFDI, utilizando un certicado del usuario (previamente guardado en la plataforma [PADE Facturación](https://facturacion.pade.mx/)).

**Formato**
CALCULAR_SELLO

**Observaciones**
* Recupera el certificado del usuario base al atributo del CFDI `NoCertificado`, en caso de no especificarse utiliza el certificado default.
* Atributo "sello" del CFDI  debe estar vacío.

#### CONSULTAR_SALDO
Esta opción retorna las transacciones disponibles del contrato enviado después de que el servicio descuente la transacción de timbrado realizada exitosamente.

**Formato**
CONSULTAR_SALDO

#### ENVIAR_AMBOS
Esta opción envía por correo electrónico los archivos XML y PDF del CFDI timbrado exitosamente, recibe el correo electrónico a donde se enviarán.

**Formato**
ENVIAR_AMBOS:correo@dominio.com

**Observaciones**
* Solo un correo electrónico por transacción de timbrado.

#### GENERAR_CBB
Esta opción te permite generar el código QR del CFDI timbrado codificado en base 64.

**Formato**
GENERAR_CBB

#### GENERAR_PDF
Esta opción retorna el PDF generado del CFDI timbrado en un arreglo de bytes codificado en base 64. 

**Formato**
GENERAR_PDF

#### OBSERVACIONES
Esta opción recibe las observaciones códificadas en base 64 que se agregan unicamente al PDF del CFDI sin afectar el contenido del XML del CFDI.

**Formato**
OBSERVACIONES:observaciones_base64

#### REGRESAR_CON_ERROR_307_XML
Esta opción indica que el XML del CFDI que se envía fue previamente timbrado, retorna la respuesta completa del timbrado previo.

**Formato**
REGRESAR_CON_ERROR_307_XML

#### REGRESAR_CADENA_ORIGINAL
Esta opción retorna la cadena original del timbre fiscal del comprobante.

**Formato**
REGRESAR_CADENA_ORIGINAL

### Response 
```xml
<servicioTimbrado>
	<id/>
	<timbradoOk/>
	<contrato/>
	<codigo/>
	<mensaje/>
	<version/>
	<UUID/>
	<FechaTimbrado/>
	<selloCFD/>
	<noCertificadoSAT/>
	<selloSAT/>
	<xmlBase64/>
	<cbbBase64/>
	<pdfBase64/>
	<saldo/>
</servicioTimbrado>
```
### `<servicioTimbrado/>`

| Atributo         | Requerido |Tipo    | Descripción |
| ---------------- |:----------|:------- |:----------- |
| id               | Si          | String  | Identificador interno en formato UUID, sin relación alguna al CFDI (informativo). |
| timbradoOk       | Si          | boolean | Indica si la invocación del método fue concluida exitosamente. |
| contrato         | Si          | String  | Contrato de Pade Timbrado Fiscal con el que se efectuó  la operación (informativo).
| codigo           | Si          | String  | Código de la operación del servicio [Códigos del servicio](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigos.md). / Código de la validación definido por el SAT. |
| mensaje          | Condicional | String | En caso de que haya un error, se devolverá la descripción del mismo. De existir más de uno estos son separados por el carácter  pipe (\|). |
| version          | Condicional | String | Versión del Timbre Fiscal Digital generado, elemento del nodo <tfd:TimbreFiscalDigital> del CFDI. Retornado cuando la transacción es exitosa. |
| UUID             | Condicional | String | Folio fiscal asignado al CFDI timbrado, elemento del nodo <tfd:TimbreFiscalDigital> del CFDI. Retornado cuando la transacción es exitosa.|
| FechaTimbrado    | Condicional | String | Fecha de timbrado del CFDI, elemento del nodo <tfd:TimbreFiscalDigital> del CFDI.  Retornado cuando la transacción es exitosa.|
| selloCFD         | Condicional | String | Sello del CFDI timbrado, elemento del nodo <tfd:TimbreFiscalDigital> del CFDI.  Retornado cuando la transacción es exitosa.|
| noCertificadoSAT | Condicional | String | Número del certificado del SAT con el que se timbra el CFDI, elemento del nodo <tfd:TimbreFiscalDigital> del CFDI. Retornado cuando la transacción es exitosa. |
| selloSAT         | Condicional | String | Sello del timbre fiscal digital del CFDI timbrado, elemento del nodo <tfd:TimbreFiscalDigital> del CFDI. Retornado cuando la transacción es exitosa. |
| xmlBase64        | Condicional | String | XML del CFDI timbrado codificado en base 64. Retornado cuando la transacción es exitosa. |
| cbbBase64        | Condicional | String | Código QR del CFDI timbrado codificado en base 64. Retornado cuando la transacción es exitosa  y se utiliza  la opción `GENERAR_CBB`.|
| pdfBase64        | Condicional | String | PDF del CFDI timbrado en un arreglo de bytes codificado en base 64. Retornado cuando la transacción es exitosa  y se utiliza  la opción `GENERAR_PDF`. |
| saldo            | Condicional | String | Transacciones disponibles para el contrato con el que se autentificó el usuario. Retornado cuando la transacción es exitosa y se utiliza la opción `CONSULTAR_SALDO`.

**Nota**: Se define como transacción de timbrado exitosa cuando el atributo `timbradoOk` es `true` y el atributo `codigo` es `0`.

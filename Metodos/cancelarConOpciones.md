# cancelarConOpciones

El método *cancelarConOpciones* crea una solicitud de cancelación para uno o más Comprobantes Fiscales Digitales por Internet (CFDI) con opciones adicionales para el servicio.

El 1 de noviembre del 2018 los servicios de cancelación se actualizaron. Las facturas en algunos casos, solo podrán cancelarse cuando el receptor de la factura acepte dicha cancelación. Te recomendamos consultar el nuevo esquema de cancelación.

## Request

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:cancelarConOpciones>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <rfcEmisor>?</rfcEmisor>
         <!--Zero or more repetitions:-->
         <arregloUUID>?</arregloUUID>
         <cert>cid:1144384445270</cert>
         <key>cid:157209680266</key>
         <keyPass>?</keyPass>
         <opciones>?</opciones>
      </tim:cancelarConOpciones>
   </soapenv:Body>
</soapenv:Envelope>
```

### Parámetros

| Atributo      | Requerido   | Tipo      | Descripción |
| ------------- |:----------- |:--------- |:----------- |
| contrato      | Si          | String    | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si          | String    | Usuario con el que se autenticará en el servicio. |
| passwd        | Si          | String    | Contraseña del usuario con el que se autenticará en el servicio. |
| rfcEmisor     | Si          | String    | RFC del emisor al que pertenecen los CFDI a cancelar. |
| arregloUUID   | Si           |String[]   | UUID, RFC Receptor, RFC Emisor y Total del CFDI a cancelar, separada por el carácter pipe (\|). **Ejemplo**: <arregloUUID>UUID\|RFC_Receptor\|RFC_Emisor\|Total</arregloUUID> |
| cert          | Condicional | byte[]   | Certificado de Sello Digital (CSD). Debe ser el mismo con el que se genero el sello digital de los CFDI a cancelar. |
| key           | Condicional | byte[]   | Llave privada del CSD. |
| keyPass       | Condicional | String   | Contraseña de la llave privada del CSD. |
| opciones      | Si          | String[] | Opciones para el servicio de cancelación. |

### Opciones

#### CERT_DEFAULT  
Esta opción utiliza el certificado default del usuario (previamente guardado en la plataforma [PADE Facturación](https://facturacion.pade.mx/)).

**Formato**
CERT_DEFAULT

**Observaciones**
* Omitir parámetros *cert*, *key* y *keyPass*.

#### CONSULTAR_SALDO 
Esta opción retorna las transacciones disponibles del contrato enviado después de que el servicio descuente las cancelaciones efectivamente realizadas.

#### PKCS12     
Esta opción acepta el Certificado de sello Digital (CSD) y la Llave Privada empaquetados en un archivo con formato PKCS12 protegido mediante la contraseña de la Llave Privada códificado en base 64.

**Formato**
PKCS12:pkcs12_base64

"pkcs12_base64" corresponde al archivo PKCS12 códificado en base 64.

**Observaciones**
* Omitir parámetros *cert* y *key*.
* El alias donde se encuentran alojados el CSD y Llave Privada, debe corresponder al RFC del emisor (Mayúsculas).
* Se debe especificar el parámetro keyPass. Esta contraseña es la que se emplea para leer el archivo PKCS12 y debe corresponder a la contraseña de la llave privada del emisor.

#### XML_CANCELACION 

Esta opción acepta el XML de cancelación firmado con el Certificado de Sello Digital del emisor de los CFDI codificado en base 64.

**Formato**
XML_CANCELACION:xml_base64

**Observaciones**
* Omitir parámetros *cert*, *key* y *keyPass*.
* Un XML de cancelación por petición
* No compatible con la opción *CERT_DEFAULT*

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
  <saldo/>
</servicioCancel>
```

### `<servicioCancel/>`

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
| saldo         | int           | Transacciones disponibles para el contrato con el que se autentifico el usuario. Retornado unicamente cuando la transacción es exitosa. |

### `<cancelacion/>`
| Atributo      | Tipo          | Descripción |
| ------------- |:------------- |:----------- |
| uuid          | string        | UUID del CFDI procesado. | https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigosCancelacion.md
| codigo        | string        | El código del servicio de cancelación. [Códigos de cancelación](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigosCancelacion.md)
| mensaje       | string        | En caso de que haya un error, se devolverá la descripción del mismo. |

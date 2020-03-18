
# consultarEstatusComprobante

El método consultarEstatusComprobante recibe los datos de un  Comprobante Fiscal Digital por Internet (CFDI), retorna el estatus del CFDI ante el SAT. 

El 1 de noviembre del 2018 los servicios de cancelación se actualizaron. Las facturas en algunos casos, solo podrán cancelarse cuando el receptor de la factura acepte dicha cancelación. Te recomendamos consultar el nuevo esquema de cancelación y utilizar este método después de crear una solicitud de cancelación para confirmar el estatus del CFDI.

## Request 

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:consultarEstatusComprobante>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <uuid>?</uuid>
         <rfcEmisor>?</rfcEmisor>
         <rfcReceptor>?</rfcReceptor>
         <total>?</total>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:consultarEstatusComprobante>
   </soapenv:Body>
</soapenv:Envelope>
```

### Parámetros

| Atributo      | Requerido | Tipo     | Descripción |
| ------------- |:--------- |:-------- |:----------- |
| contrato      | Si        | String   | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | String   | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | String   | Contraseña del usuario con el que se autenticará en el servicio. |
| uuid          | Si        | String   |             |
| rfcEmisor     | Si        | String   |             |
| rfcReceptor   | Si        | String   |             |
| total         | Si        | String   |             |
| opciones      | Si        | String[] |             |

## Response

```xml 
<servicioConsultaComprobante>
	<consultaOk/>
	<codigo/>
	<codigoEstatus/>
	<esCancelable/>
	<estado/>
	<estatusCancelacion/>
  <codigoEstatusCancelacion/>
  <estatusCfdi/>
  <mensaje/>
</servicioConsultaComprobante>
```

### `<servicioConsultaComprobante/>`

| Atributo              | Tipo    | Descripción |
| --------------------- |:------- |:----------- |
| consultaOk            | boolean | Indica si la invocación del método fue concluida exitosamente. |
| mensaje               | String  | En caso de que haya un error, se devolverá la descripción del mismo. |
| codigo                | String  | Código de respuesta del servicio del SAT. [Códigos](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigosCancelacion.md) |
| codigoEstatus         | String  | Descripción del código de respuesta del servicio del SAT. |
| esCancelable          | String  | Indica como se cancelará el comprobante. |
| estado                | String  | Estatus del CFDI. |
| estatusCancelacion    | String  | Indica como se canceló el CFDI si se encuentre cancelado. |
| codigoEstatusCancelacion | String | Código estatus cancelación.|
| estatusCfdi           | int     | Estatus del CFDI ante el SAT. [Códigos estatus CFDI](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigoEstatusCfdi.md)|


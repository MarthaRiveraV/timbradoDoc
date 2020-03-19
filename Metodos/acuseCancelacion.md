# Método: acuseCancelacion


El método *acuseCancelacion* recibe el UUID (Folio fiscal) de un Comprobante Fiscal Digital por Internet (CFDI) previamente cancelado, retorna el acuse de cancelación proporcionado por el SAT codificado en base64.

## Request

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:acuseCancelacion>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <uuid>?</uuid>
      </tim:acuseCancelacion>
   </soapenv:Body>
</soapenv:Envelope>
```

### Parámetros

| Atributo      | Requerido | Tipo   | Descripción |
| ------------- |:--------- |:------ |:----------- |
| contrato      | Si        | String | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | String | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | String | Contraseña del usuario con el que se autenticará en el servicio. |
| uuid          | Si        | String | Folio fiscal del comprobante del que se desea recuperar el acuse de cancelación. |


## Response 

```xml
<servicioConsulta>
  <contrato/>
  <consultaOk/>
  <codigo/>
  <xmlBase64/>
  <mensaje/>
</servicioConsulta>
```

### `<servicioConsulta/>`

| Atributo      | Tipo      | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | string    | Contrato de Pade Timbrado Fiscal enviado por el usuario (informativo). |
| consultaOk    | boolean   | Indica si la operación fue concluida exitosamente. |
| codigo        | string    | Código del servicio de consulta. [Códigos del servicio](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigos.md)
| xmlBase64     | string    | XML del acuse de cancelación del SAT, códificado en base64.
| mensaje       | string    | En caso de que haya un error, se devolverá la descripción del mismo. |


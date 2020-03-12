# Acuse Cancelación


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

| Atributo      | Requerido | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | Si        | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | Contraseña del usuario con el que se autenticará en el servicio. |
| uuid          | Si        | Folio fiscal del comprobante del que se desea recuperar el acuse de cancelación. |

```xml
<servicioConsulta>
  <contrato></contrato>
  <consultaOk><consultaOk>
  <codigo></codigo>
  <xmlBase64></xmlBase64>
  <mensaje></mensaje>
</servicioConsulta>
```

| Atributo      | Tipo      | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | string    | El contrato de Pade Timbrado Fiscal enviado por el usuario (informativo). |
| consultaOk    | boolean   | Indica si la operación de timbrado fue concluida exitosamente. |
| codigo        | string    | El código del servicio de consulta. [Códigos del servicio](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigos.md)
| xmlBase64     | string    | XML del acuse de cancelación del SAT, códificado en base64.
| mensaje       | string    | En caso de que haya un error, se devolverá la descripción del mismo. |


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
| contrato      | string    |
| consultaOk    | boolean   |
| codigo        | string    |
| xmlBase64     | string    |
| mensaje       | string    |

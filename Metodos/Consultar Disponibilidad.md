## consultarDisponibilidadServicio

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:consultarDisponibilidadServicio>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
      </tim:consultarDisponibilidadServicio>
   </soapenv:Body>
</soapenv:Envelope>
```

| Atributo      | Requerido | Descripción |
| ------------- |:--------- |:----------- |
| contrato      | Si        | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | Contraseña del usuario con el que se autenticará en el servicio. |

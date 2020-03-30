# consultarDisponibilidadServicio

El método consultarDisponibilidadServicio permite autentificarse ante el servicio con el objetivo de verificar la disponibilidad y acceso al servicio.

## Request

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

### Parámetros

| Atributo      | Requerido | Tipo   | Descripción |
| ------------- |:--------- |:------ |:----------- |
| contrato      | Si        | String | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | String | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | String | Contraseña del usuario con el que se autenticará en el servicio. |

## Response 

```xml
<consultarDisponibilidadServicioResponse>
  <servicioOk/>
</consultarDisponibilidadServicioResponse>
```

### `<consultarDisponibilidadServicioResponse/>`

| Atributo      | Tipo      | Descripción |
| ------------- |:--------- |:----------- |
| servicioOk    | boolean   | Indica si el servicio se encuentra disponible. |




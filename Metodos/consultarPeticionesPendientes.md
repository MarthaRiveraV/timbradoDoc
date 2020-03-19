# consultarPeticionesPendientes

El método *consultarPeticionesPendientes* recibe el RFC de un contribuyente, retorna las peticiones pendientes de cancelación que tiene el contribuyente como receptor de Comprobantes Fiscales Digitales por Internet (CFDI).

## Request

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tim="timbrado.ws.pade.mx">
   <soapenv:Header/>
   <soapenv:Body>
      <tim:consultarPeticionesPendientes>
         <contrato>?</contrato>
         <usuario>?</usuario>
         <passwd>?</passwd>
         <rfcReceptor>?</rfcReceptor>
         <!--Zero or more repetitions:-->
         <opciones>?</opciones>
      </tim:consultarPeticionesPendientes>
   </soapenv:Body>
</soapenv:Envelope>
```

### Parámetros

| Atributo      | Requerido | Tipo     | Descripción |
| ------------- |:--------- |:-------- |:----------- |
| contrato      | Si        | String   | Contrato de Pade Timbrado Fiscal. | 
| usuario       | Si        | String   | Usuario con el que se autenticará en el servicio. |
| passwd        | Si        | String   | Contraseña del usuario con el que se autenticará en el servicio. |
| rfcReceptor   | Si        | String   | RFC del contribuyente del que se desea consultar las peticiones de cancelación que tiene como receptor de los CFDI. |
| opciones      | Si        | String[] | Opciones para el servicio. |        

## Response

```html
  <servicioPeticionesPendientes>
	<consultaOk/>
	<codigo/>
	<codigoEstatus/>
	<uuids>
		<uuid/>
	</uuids>
	</servicioPeticionesPendientes>
```

### `<servicioPeticionesPendientes/>`

| Atributo      | Tipo     | Descripción |
| ------------- |:-------- |:----------- |
| consultaOk    | boolean  | Indica si la invocación del método fue concluida exitosamente. |
| codigo        | String   | El código del servicio de consulta. [Códigos del servicio](https://github.com/MarthaRiveraV/timbradoDoc/blob/master/codigos.md) |
| codigoEstatus | String   | Descripción del código. |
| uuids         | uuid[]   | Nodo que expresa los UUID. |
| uuid          | String   | Folio fiscal del CFDI del que se solicita aceptación por parte del contribuyente para su cancelación. |
| mensaje       | String   | En caso de que haya un error, se devolverá la descripción del mismo. | 

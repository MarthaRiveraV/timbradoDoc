
# Códigos de respuesta

| Código | Descripción |
| :----: | :---------------------------------------------------------------------------------------------- |
| 0      | Timbrado exitoso. |
| 1      | El usuario del webservice no existe o proporcionó una contraseña incorrecta. |
| 2	     | Contrato inválido. El contrato está expirado, o no cuenta con servicio de timbrado. |
| 3	     | Parámetro inválido. Uno de los parámetros de la operación del webservice es incorrecto o hace falta.|
| 5	     | Off-line por mantenimiento. |
| 7	     | El servicio de CancelaciónSAT no está disponible, intente más tarde. |
| 20	   | El usuario no cuenta con un certificado default. |
| 21	   | CFDI sin cancelar. Aplica a la consulta de acuse de cancelación. |
| 201	   | Comprobante cancelado exitosamente. (sin autorización) |
| 202	   | El comprobante ya ha sido previamente cancelado. |
| 203	   | El RFC del emisor no corresponde. |
| 205    | El UUID no existe. |
| 301	   | XML mal formado. |
| 302	   | Sello mal formado o inválido. |
| 303	   | Sello no corresponde al emisor. |
| 304    | Certificado revocado o caduco. |
| 305	   | La fecha de emisión no está dentro de la vigencia del CSD del emisor. |
| 306	   | El certificado no es de tipo CSD. |
| 307	   | El CFDI contiene un timbre previo. |
| 308	   | Certificado no expedido por el SAT. |
| 401	   | Fecha y hora de generación fuera de rango. |
| 402	   | El RFC del emisor no se encuentra en el régimen de contribuyentes. |
| 403    | La fecha de emisión no es posterior al 1 de enero de 2012. |
| 602	   | CFDI no existe. |

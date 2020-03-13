
# Códigos de respuesta cancelación

| Código | Descripción |
| :----: | :---------------------------------------------------------------------------------------------- |
| 90     | N – 602: Comprobante no encontrado. Este código tiene lugar cuando un comprobante no ha sido encontrado en la base de datos del SAT. |
| 91     | S – Comprobante obtenido satisfactoriamente. Este código tiene lugar cuando el comprobante consultado se encuentra en la base de datos del SAT. |
| 92     | N – 601: La expresión impresa proporcionada no es válida. Este código tiene lugar cuando alguno de los parámetros enviados para la consulta del estatus del comprobante es erróneo. |
| 93	   | Indeterminado. Este código tiene lugar cuando el SAT actualizó algún elemento en la respuesta del servicio de consulta de comprobantes y dicho elemento no es reconocido por Prodigia. |
| 94	   | No Cancelable. Este código comúnmente aparecerá cuando el comprobante que se desea cancelar contenga al menos un cfdi relacionado vigente. |
| 95	   | Cancelado con aceptación. Este código aparecerá una vez que el cfdi está cancelado y requirió de autorización por parte del receptor para ser cancelado. |
| 96	   | En proceso. Este código aparecerá cuando se intenta enviar una nueva solicitud de cancelación de un comprobante que previamente intentó ser cancelado y dicha solicitud requiere de aceptación por parte del receptor. |
| 97	   | Solicitud rechazada. Este código aparecerá cuando el receptor rechaza la cancelación de algún comprobante, para este caso el cfdi queda con estado vigente. |
| 98	   | Plazo vencido. Este código aparecerá cuando exista una solicitud de cancelación que requiera de aceptación por parte del receptor, y tras pasar las 72 horas, no se obtuvo respuesta alguna. En este caso el cfdi se cancela dando por hecho que la cancelación fue aceptada. |
| 99	   | Límite máximo alcanzado. Pendiente por definir. |
| 201	   | Cancelado sin aceptación. Este  código aparecerá cuando el cfdi se canceló sin necesidad de que el receptor autorice, básicamente funciona de manera unilateral. |
| 202	   | El comprobante ya ha sido previamente cancelado. |
| 203    | El RFC del emisor no corresponde. |

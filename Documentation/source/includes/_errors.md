# Códigos HTTP

En esta API se utilizan los siguiente código HTTP


Código | Significado
---------- | -------
400 | Solicitud incorrecta – Solicitud invalida
401 | No autorizado – Clave del API incorrecta
403 | Prohibido -- El recurso solicitado está oculto solo para administradores.
404 | No encontrado – El recurso especifico no fue encontrado
405 | Método no permitido -- Se trató de acceder al recurso con un método invalido
406 | Inaceptable -- Se solicitó un formato que no es json
410 | Quitado -- El recurso solicitado fue removido de los servidores
418 | Soy una tetera
429 | Muchas solicitudes -- Se solicitaron muchos recursos
500 | Error de servidor interno -- Existe un problema con el servidor, intenta más tarde
503 | Servicio no disponible -- Estamos temporalmente fuera de servicio por mantenimiento, por favor intente mas tarde

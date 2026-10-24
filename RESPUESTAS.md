# Respuestas del parcial

1. El límite inferior permitía `stock=0`; lo cambié a `ge=1`, de acuerdo con la regla de 1 a 50 unidades.

2. Faltaba confirmar la transacción con `session.commit()`. Ahora se agrega, se confirma y luego se actualiza el objeto con `session.refresh()` para obtener el ID generado.

3. Declaraba una respuesta de un solo `GameResponse`, aunque el servicio devuelve varios juegos. El modelo de respuesta ahora es `list[GameResponse]`.

4. Si `session.get()` no encuentra el juego, el servicio ahora lanza `HTTPException` con estado 404 y detalle `Game not found`.

5. `session.delete()` marcaba el objeto para borrar dentro de la sesión, pero faltaba confirmar la transacción. Añadí `session.commit()` después de eliminarlo.

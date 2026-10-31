# ElitePS3 — roadmap de trabajo

## Estado

- Proyecto de trabajo derivado del port RPCS3 para PS4 0.40.
- Rama de trabajo: `eliteps3/initial-audit`.
- Esta rama conserva `main` intacta.
- Esta primera entrega es documentación de auditoría; todavía no modifica el emulador ni genera un PKG.

## Objetivo

Preparar una compilación experimental identificada como **ElitePS3**, priorizando estabilidad y compatibilidad en PS4 con GoldHEN. Mejorar el rendimiento solo mediante cambios medibles y sin prometer 60 FPS cuando el hardware o el juego no lo permitan.

## Hardware de referencia

- PS4 Slim.
- Firmware informado: 13.52.
- GoldHEN.
- Juego de prueba: Castlevania: Lords of Shadow para PS3.

## Síntomas observados en la prueba inicial

- El juego inicia y permite jugar.
- Rendimiento general muy lento.
- FPS variables.
- Cierres inesperados (crashes).

No se han recibido todavía los registros de la sesión, por lo que no se atribuye el fallo a un componente concreto.

## Plan de trabajo

1. **Congelar una línea base:** registrar versión exacta del port, configuración del juego, punto de prueba y síntomas reproducibles.
2. **Analizar registros:** revisar `/data/rpcs3/startup.log`, `/data/rpcs3/log/RPCS3.log` y `/data/rpcs3/log/mesa.log`. El usuario debe revisar y ocultar nombres de usuario u otros datos personales antes de compartirlos.
3. **Auditar rutas críticas:** administración de hilos, memoria, PPU/SPU, RSX/Vulkan y audio; relacionar cada hipótesis con evidencia de logs o código.
4. **Cambios pequeños y aislados:** cada cambio debe tener hipótesis, prueba de regresión y comparación con la línea base.
5. **Compilar y validar:** ejecutar las pruebas host disponibles y generar el PKG únicamente desde una compilación reproducible y validada.
6. **Prueba en consola:** comparar arranque, menú, combate, transiciones, audio, estabilidad y duración de sesión.

## Criterios de aceptación de la primera prueba

- El PKG se instala y arranca en la PS4 de referencia.
- La identidad visual/nombre de la aplicación es ElitePS3 sin alterar indebidamente el identificador de título o los requisitos de GoldHEN.
- Se documentan FPS/fluidez observados, fallos gráficos, audio y cualquier cierre.
- No se declara una mejora sin comparación con la versión base.

## Restricciones técnicas y legales

- El port es experimental y la velocidad depende del juego y del hardware Jaguar de PS4.
- No se incluyen juegos, firmware de PS3, claves ni licencias.
- Se conserva la licencia GPL-2.0 y los avisos de terceros.
- No se cambiará el ID de título ni los metadatos de instalación hasta verificar las implicaciones de compatibilidad y actualización.
- Un nombre nuevo o un PKG recompilado no implica por sí solo mejoras de rendimiento.

## Primeros archivos que deben revisarse

- `BUILDING.md`
- `rpcs3-ps4/ps4-port/TESTAR_NO_PS4.txt`
- `rpcs3-ps4/ps4-port/package-native.ps1`
- Código PS4 relacionado con presupuesto de memoria, planificación de hilos y políticas de configuración por juego.

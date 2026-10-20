# GYM-OS · Material de estudio del equipo

**Para la preentrega, estudien la carpeta `preentrega/`.** Cada integrante tiene una guía con un mapa visual, su funcionalidad, archivos, funciones, librerías, datos, errores y demostración. Tomás tiene inteligencia artificial; no se le suma otro módulo.

Este repositorio contiene documentación de estudio, no la aplicación ni claves privadas. El reparto organiza responsabilidades de preparación y revisión; no atribuye desarrollos históricos que no se realizaron.

## Qué estudia cada uno para la preentrega

| Integrante         | Funcionalidad                             | Guía individual                                         |
| ------------------ | ----------------------------------------- | ------------------------------------------------------- |
| Gianluca Pizarro   | Acceso y recuperación                     | [Abrir guía](preentrega/guias/01-gianluca-pizarro.md)   |
| Tomás Menossi      | Chat con inteligencia artificial          | [Abrir guía](preentrega/guias/02-tomas-menossi.md)      |
| Iván Lerner        | Entrenamientos e historial                | [Abrir guía](preentrega/guias/03-ivan-lerner.md)        |
| Paulo López        | Objetivos personales                      | [Abrir guía](preentrega/guias/04-paulo-lopez.md)        |
| Gade Silva y Lápiz | Mediciones y perfil físico                | [Abrir guía](preentrega/guias/05-gade-silva-y-lapiz.md) |
| Valentín Schueld   | Rutinas manuales                          | [Abrir guía](preentrega/guias/06-valentin-schueld.md)   |
| Mateo Romani       | Panel y visualización del progreso        | [Abrir guía](preentrega/guias/07-mateo-romani.md)       |
| Joaquín Casanou    | Catálogo y consulta de ejercicios/rutinas | [Abrir guía](preentrega/guias/08-joaquin-casanou.md)    |
| Simón Castellani   | Mi cuenta y datos personales              | [Abrir guía](preentrega/guias/09-simon-castellani.md)   |

## Por dónde empezar

1. Todos leen [conceptos compartidos](CONCEPTOS-COMUNES.md) y [recorrido común de la preentrega](preentrega/guias/README.md).
2. Cada persona empieza por el mapa visual de su guía: sigue las flechas desde la pantalla hasta los datos y el resultado. Después abre sus archivos y sigue las funciones enlazadas.
3. Practican la demostración del módulo y responden las preguntas de defensa.
4. Ensayan juntos el [orden de exposición](preentrega/REPARTO.md#orden-de-demostración), sin memorizar el código palabra por palabra.
5. Consultan el [alcance de la preentrega](preentrega/docs/ALCANCE.md): aproximadamente la mitad del sistema final, con límites explícitos.

Las guías enlazan a archivos y líneas de commits concretos de los repositorios de código. No hace falta buscar a ciegas dentro de cada archivo. Las referencias están en [REFERENCIAS.json](REFERENCIAS.json); si el código cambia, hay que revisar estos enlaces antes de estudiar otra versión.

## Material del sistema final

La carpeta `final/` queda como referencia para la entrega completa: [reparto final](final/REPARTO.md) y [nueve guías finales](final/guias/README.md). **No mezclar repartos:** Valentín, Mateo y Simón tienen funcionalidades distintas en la preentrega porque nutrición y administración quedaron para el final. Tomás conserva IA en ambas; en la parcial solo hay chat, en la final también generación/adaptación de planes.

Código de la preentrega: [GYM-OS-Preentrega](https://github.com/tomimeno0/GYM-OS-Preentrega). Código completo: [GYM-OS](https://github.com/tomimeno0/GYM-OS).

## Qué tiene que poder demostrar cada uno

- Ubicar la pantalla, la ruta de API, el controlador y las tablas de su función.
- Explicar qué recibe una función, qué comprueba y qué devuelve.
- Ejecutar un caso válido y un rechazo; cancelar una acción cuando corresponda.
- Recargar y mostrar que los datos guardados siguen presentes.
- Explicar el límite con el módulo del compañero, sin estudiar todo el sistema.

No compartir contraseñas ni API keys al proyectar o estudiar. Usar cuentas ficticias. El correo de desarrollo no llega a un buzón y una respuesta simulada no prueba Cohere real. El alcance y resultados comprobados están documentados por versión.

## Cómo leer los mapas

Los bloques `mermaid` se dibujan como diagramas al abrir los archivos Markdown en GitHub. Usá la vista previa, no la vista de código. Las flechas continuas indican el recorrido; las punteadas señalan un aporte de contexto o una conexión entre módulos. Cada bloque muestra archivos y funciones reales de su versión, junto con validaciones y errores relevantes. Son mapas de estudio simplificados; no sustituyen los UML ni los diagramas de secuencia del proyecto.

Hay un mapa en cada una de las 18 guías individuales y otro en cada recorrido común. El de Tomás en `preentrega/` conserva exactamente el diagrama del chat que se mostró en la conversación. Los mapas de `final/` mantienen su alcance separado.

# Juegos Opos — web de estudio (Técnico de Hacienda)

## Cómo abrirla
- **Ordenador**: doble clic en `index.html`.
- **Móvil (ya)**: copia toda la carpeta `_Web` al teléfono y abre `index.html`; en el menú del navegador,
  "Añadir a pantalla de inicio".
- **Móvil como app de verdad (PWA)**: cuando la subamos a internet (ver más abajo), se instala con icono
  y funciona offline.
> Mantén juntos en la misma carpeta: `index.html`, `datos.js`, `contenido.js`, `sw.js`, `manifest.json`,
> `icon-192.png`, `icon-512.png`. El progreso (errores, repetición espaciada, racha, estadísticas) se
> guarda en el navegador del dispositivo.

## Secciones y modos
- **⭐ Empieza aquí**: Repaso del día (mezcla tus errores + preguntas nuevas; mantiene la racha) · Temari (Moodle).
- **📚 Temari (Moodle)**: cada tema en **texto completo normal** (no esquemático) + 🔊 leer en voz alta,
  y al final botones de **Test / Cloze / Flashcards de ese tema**.
- **📝 Examen 1 (test)**: Simulacro AEAT (−1/3 por fallo, cronómetro, informe por bloques) · Test por bloque/tema.
- **📒 Examen 2 (Contabilidad)**: Test y Flashcards de conceptos *(los asientos se practican con los supuestos oficiales)*.
- **🎓 Examen 3**: Pregunta de TODO · Explica un tema (autoevaluación con guión) · Casos prácticos.
- **🧠 Memorización**: Cloze de cifras/plazos · Cloze legal *(con opción «estudia y tapa»)* · Flashcards SRS (Leitner) · ¿Qué artículo/ley? · Mapa mental (desbloqueas epígrafes acertando).
- **🔍 Comprensión**: Detección de errores · Comparación rápida · Ordenar / reconstruir · Dictado conceptual.
- **🏆 Competición con Judith**: Reto diario (mismas preguntas para los dos) · Clasificación (ranking hoy/semana/total). *Requiere configurar Firebase — ver `GUIA_ONLINE.md`.*
- **🎲 Más juegos**: Supervivencia (3 vidas) · Emparejar · Verdadero/Falso · Tabla completa · Boss del bloque (medalla).
- **📊 Progreso**: Banco de errores · Estadísticas (racha, logros, puntos débiles por tema).

> «Explica un tema» incluye **🎙️ grabar tu explicación** y reproducirla. Botones **🔊** leen en voz alta (test, temario).

Todo (cloze, errores, comparación, temario…) sale **verbatim de tus apuntes** (no de la versión de audio):
el cloze muestra el **párrafo completo** y solo oculta **plazos, % e importes** (nunca artículos ni nº de tema).

## Regenerar los datos
```
python work/study/build_web_data.py    # juegos (test, cloze, errores, comparación, procedimientos, temas…)
python work/study/build_contenido.py   # contenido del Temario (Moodle)
```

## Ponerla ONLINE (clasificación + app instalable)
Todo el código ya está listo. Solo faltan tus cuentas. **Pasos detallados en `GUIA_ONLINE.md`:**
1. **Firebase** (ranking con Judith): registra una app Web en tu proyecto, copia el `firebaseConfig` y
   pégalo en `firebase-config.js` (o pásamelo y lo dejo puesto). Publica las reglas de Firestore de la guía.
2. **GitHub Pages** (app instalable): sube la carpeta `_Web` con GitHub Desktop y activa Pages.

Mientras no configures Firebase, todo funciona en local; «Reto diario/Clasificación» avisan de que falta la config.

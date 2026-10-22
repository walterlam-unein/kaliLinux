# Kali Aula · Escritorio virtual de seguridad

## Abrir y empezar

1. Extrae todo el ZIP y abre la carpeta `Kali_Aula`.
2. Abre `index.html`. Conserva `app.js`, `styles.css` y `config.js` a su lado.
3. Escribe en la terminal el comando indicado a la derecha y pulsa **Enter**. La guía comprueba el resultado y avanza automáticamente.
4. Al terminar la preparación, selecciona uno de los cinco talleres en el panel derecho.
5. Realiza las acciones escritas, observa el resultado en el navegador del escritorio y aplica la defensa indicada.
6. Añade tu nombre o alias desde la derecha. Al completar la práctica, abre **Preguntas**, responde las tres y califica.
7. Abre o cierra **Reporte del taller** y **Todas las notas /10** desde ese mismo panel.

La página está compilada: para usarla no se necesita instalar Node, React, Docker ni Kali. El entorno completo funciona en el navegador, con archivos y servicios ficticios locales. No hay sección de código fuente en el recorrido del estudiante.

## Qué representa esta computadora

La primera pantalla es un equipo anfitrión con Docker simulado. La preparación distingue una imagen, un contenedor y una shell dentro del contenedor. Después se abre un escritorio didáctico inspirado en Kali con Xfce: barra de aplicaciones, iconos, ventanas, terminal, explorador Thunar, editor Mousepad y navegador social.

**Docker no es una máquina virtual completa.** Los contenedores comparten el kernel del anfitrión. La imagen oficial de Kali no abre por sí sola un escritorio gráfico. En un contenedor real se necesitan componentes y configuración gráfica adicionales. Aquí `aula escritorio` representa esa capa: es un comando inventado exclusivamente para esta actividad.

Kali es una distribución de Linux orientada a auditoría y pruebas de seguridad. No concede acceso a cuentas por instalarla. Su uso ético requiere permiso, alcance definido, evidencias y corrección de fallos. El **Manual de Kali**, accesible a la derecha o desde el escritorio, desarrolla estos conceptos y compara los cinco mecanismos.

## Preparación inicial: siete acciones escritas

Escribe una por una en la terminal de la página, no en la terminal de tu computadora:

```text
docker --version
docker pull kalilinux/kali-rolling
docker run -dit --name kali-aula kalilinux/kali-rolling bash
docker exec -it kali-aula bash
apt update
apt install -y kali-desktop-xfce
aula escritorio
```

La sintaxis de Docker y apt corresponde a operaciones reales, pero aquí solo cambia el estado del simulador. No se descargan imágenes ni paquetes. `apt update` actualiza índices; no equivale a actualizar todos los paquetes instalados.

La instalación se conserva en el mismo navegador y dirección. El cambio de estudiante conserva la preparación de Kali; las nuevas prácticas comienzan sin las evidencias de la persona anterior.

## Manejar las ventanas

- Abre aplicaciones con un clic en el icono, desde **Aplicaciones**, la barra superior o los accesos de la derecha.
- Arrastra la barra de título para mover una ventana. Sus botones permiten minimizar, maximizar y cerrar.
- Un doble clic en el título maximiza o restaura. En escritorio, la esquina inferior derecha permite cambiar el tamaño.
- Las ventanas minimizadas vuelven a abrirse desde la barra inferior. **Mostrar escritorio** minimiza las abiertas.
- Cerrar terminal, preguntas o reportes no borra el avance. Los borradores del editor se conservan al cerrar la ventana durante esa sesión; guarda antes de recargar la página.
- El botón de pantalla completa ayuda a presentar el entorno como un sistema operativo. También puede usarse F11 en navegadores que lo admitan.
- En pantallas estrechas las ventanas se ajustan al ancho disponible y la guía pasa debajo del escritorio. Para trabajar con consola y guía simultáneas se recomienda una computadora.

## Terminal y archivos

La consola interpreta un catálogo limitado de comandos, sin ejecutar scripts ni procesos reales.

| Acción | Ejemplo dentro del simulador |
| --- | --- |
| Mostrar ubicación | `pwd` |
| Listar archivos | `ls` |
| Cambiar de taller por ruta | `cd /root/laboratorios/session` |
| Leer un archivo | `cat mensaje.txt` |
| Abrir el editor | `mousepad politica.json` |
| Abrir la maqueta social | `firefox https://social.aula.test` |
| Elegir un caso | `aula iniciar stuffing` |
| Consultar el catálogo | `ayuda` o `aula ayuda` |
| Ver progreso | `aula estado` |
| Limpiar la consola | `clear` o Ctrl+L |
| Ver comandos usados | `history` |
| Volver al anfitrión | `exit` |
| Volver a la shell de Kali | `docker exec -it kali-aula bash` |

Las flechas arriba y abajo recuperan comandos anteriores. Pulsa Enter para ejecutar. Los errores explican la sintaxis admitida. La terminal no admite tuberías, redirecciones ni comandos de red hacia servicios externos.

Cada carpeta en `/root/laboratorios` contiene `LEEME.txt`, `politica.json`, `evidencias.log` y las muestras correspondientes. Abre un archivo desde **Archivos** o con `mousepad`. Solo `politica.json` y `candidatas.txt` son editables. En Mousepad, escribe el cambio indicado y pulsa **Guardar** o Ctrl+S; si el JSON está incompleto, el editor conserva el borrador y explica el error. Los cambios guardados afectan a la siguiente prueba.

## Los cinco talleres

| Taller | Trabajo escrito y evidencia | Comparación con una defensa |
| --- | --- | --- |
| Phishing | Leer un mensaje, identificar el dominio final `aula.invalid` y ejecutar la entrega de una muestra al destino impostor | Editar `decision` de `send` a `leave` y volver a ejecutar |
| Credential stuffing | Leer el par de la tienda ficticia PixelShop y escribir `aula acceso luna.crea Luna!26` | Editar `reuse` de `yes` a `no`; el mismo par deja de coincidir |
| Adivinación por diccionario | Leer `candidatas.txt` y ejecutar `aula diccionario candidatas.txt` | Editar `limit` de `0` a `3`; la ronda se detiene tras tres fallos |
| Secuestro de sesión / MITM | Comparar `aula trafico https` y `aula trafico http`; escribir el token observado con `aula sesion` | Ejecutar `aula revocar` y presentar la misma copia otra vez |
| Abuso de recuperación | Solicitar un enlace, leer el correo local y escribir su token con `aula restablecer` | Editar `factor` de `off` a `on`, solicitar un token nuevo y comprobar la prueba independiente |

La guía indica el comando exacto y explica qué debes modificar. No hay un botón «Siguiente» que sustituya estas acciones. Las tareas se marcan cuando se ejecuta el comando correcto, se lee la evidencia o se guarda el cambio requerido.

El navegador del escritorio muestra una maqueta inspirada en Instagram, la cuenta ficticia `luna.crea`, las respuestas del servicio y el registro de pruebas. Puede quedar detrás de la terminal para permitir seguir escribiendo; usa **Ver red social** a la derecha para traerlo al frente.

**Ampliaciones después del recorrido:** edita el orden de `candidatas.txt` y observa si una coincidencia anterior al límite consigue acceso; cambia la exigencia de segundo factor en `politica.json`; o explora `aula trafico proxy` con código o passkey en el taller de sesión. Cada política admite solo los valores descritos por el modelo. Usa **Reiniciar práctica** para restaurar los archivos de un caso; las notas calificadas se conservan.

## Límites que debe discutir la clase

- Obtener una contraseña y lograr entrar en una cuenta son hechos distintos: pueden existir verificaciones adicionales.
- Credential stuffing prueba un par ya obtenido en otro servicio. El diccionario prueba candidatas. No son el mismo origen del secreto.
- HTTPS cifra hacia el destino elegido; no vuelve legítimo un dominio impostor. Observar una red no permite leer el token de una conexión TLS válida al origen correcto.
- El ejemplo HTTP expone una cookie ficticia de un servicio inseguro: **no describe el transporte real de Instagram**. El caso opcional de proxy supone una visita al origen impostor; no representa romper TLS.
- Pasar a HTTPS no revoca una copia del token que ya se obtuvo. La revocación ocurre en el servidor del modelo.
- El diccionario procesa como máximo veinte candidatas virtuales. Cada ejecución es una ronda independiente. La pausa de tres fallos ilustra un límite; no reproduce temporizadores ni políticas antifraude de una plataforma real.
- La recuperación supone un buzón ya controlado por el impostor. Pedir el enlace no basta: debe obtenerse y seguir vigente. Los tokens nuevos sustituyen a los anteriores y un token usado no sirve otra vez.
- Los comandos `aula` son herramientas didácticas propias de esta página; no existen como herramientas oficiales de Kali. No hay capturas reales, acceso a cookies del navegador ni ataques a cuentas externas.

## Preguntas, reportes y calificación

Cada taller tiene tres preguntas de distinto estilo:

1. **Selección única:** 3 puntos por la opción correcta.
2. **Ordenamiento:** 1 punto por posición correcta, máximo 3. Usa las flechas y confirma el orden.
3. **Relación:** 1 punto por relación correcta, máximo 4.

La nota es sobre **10**. La corrección se muestra después de responder las tres preguntas. El PDF incluye preguntas, respuestas, correcciones y desglose. Es posible iniciar otro intento desde el reporte: se conservan los anteriores y el registro utiliza el más reciente. El promedio final aparece cuando existen notas de los cinco talleres; un pendiente no se convierte en cero.

Para reunir resultados de distintos equipos, cada estudiante descarga el JSON de su reporte. El docente abre **Todas las notas /10 → Registro docente → Importar resultados JSON**, selecciona los archivos y exporta el registro en PDF o CSV para Excel. La importación recalcula las notas a partir de las respuestas y evita duplicar un mismo resultado. El respaldo JSON permite trasladar el registro completo.

El avance se guarda en este navegador y dirección. No hay sincronización automática entre computadoras. Borrar datos, usar modo privado o cambiar la dirección puede separar o eliminar ese avance. Descarga los reportes y respaldos antes de terminar. Las notas anteriores de Acceso Lab conservan su formato y pueden importarse.

La evaluación es formativa: toda la lógica y las respuestas están en el cliente. No existe verificación de identidad ni protección de un examen supervisado. Identificar al estudiante con un alias evita introducir datos innecesarios.

## Publicar en un solo GitHub Pages

Sube **el contenido de `Kali_Aula`** a la raíz del repositorio. `index.html`, `app.js`, `styles.css` y `config.js` deben quedar juntos, sin otra carpeta intermedia. No basta con subir el ZIP.

En **Settings → Pages**, usa la publicación desde una rama, selecciona `main` y `/(root)`, guarda y comparte el enlace publicado. Las rutas de los recursos son relativas, por lo que sirven bajo el nombre de cualquier repositorio. `fuentes-react-vite.zip`, este manual y `TERCEROS.txt` pueden permanecer junto a la página; el ZIP de fuentes no se necesita para ejecutarla.

## Ajustes HTML + CSS + JavaScript

Abre **Ajustes** desde la derecha para configurar el curso sugerido, el nombre del docente y la lectura para proyector. Guarda los cambios localmente o descarga `config.js` para reemplazar el archivo junto a `index.html` y distribuirlos a la clase. También puedes editar ese archivo de JavaScript con un editor de texto. Los ajustes ya guardados en cada navegador tienen prioridad.

Las propiedades efectivas del escritorio son `courseName`, `teacherName` y `projector`. `showKali` y `showExperiments` se conservan por compatibilidad con el modo anterior; no ocultan el escritorio actual. Cambiar los ajustes no cambia las notas ya calificadas.

## Proyecto editable React + Vite

Extrae `fuentes-react-vite.zip` en otra carpeta. Usa Node compatible con Vite 7 (por ejemplo Node 22.12 o posterior), ejecuta `npm ci`, después `npm run dev`. Para publicar una modificación: `npm run build` y utiliza el contenido de `dist`. `npm test` comprueba los recorridos y la evaluación.

| Archivo | Responsabilidad |
| --- | --- |
| `src/os/Desktop.jsx` | Ventanas, aplicaciones, panel derecho, estudiante y conexión con notas |
| `src/os/DesktopWindow.jsx` | Arrastrar, minimizar, maximizar y cerrar |
| `src/os/machine.js` | Intérprete de comandos, Docker simulado y sistema de archivos virtual |
| `src/os/labFiles.js` | Instalación, tareas escritas y archivos iniciales |
| `src/os/Terminal.jsx` | Entrada de comandos, historial y respuestas |
| `src/os/FileManager.jsx` | Explorador y editor de archivos |
| `src/os/LabBrowser.jsx` | Maqueta social y evidencias del servicio |
| `src/os/desktop.css` | Apariencia del sistema operativo y adaptación de pantalla |
| `src/content.js`, `src/learning.js` | Textos, preguntas y mecanismos conceptuales |
| `src/scenarioEngine.js` | Reglas de los escenarios, sin red |
| `src/grading.js`, `src/Reports.jsx`, `src/reports.js` | Cálculo, importación y exportación PDF/CSV/JSON |
| `public/config.js`, `src/Configuration.jsx` | Ajustes de presentación |

La entrada principal es `src/main.jsx`. El proyecto conserva los componentes anteriores como referencia; la página compilada abre únicamente el escritorio nuevo. Los estilos de documentos y las tipografías de PDF se reutilizan. Consulta `TERCEROS.txt` para licencias y atribuciones.

## Referencias

- Kali y Docker: https://www.kali.org/docs/containers/using-kali-docker-images/
- Imágenes oficiales: https://www.kali.org/docs/containers/official-kalilinux-docker-images/
- Xfce en Kali: https://www.kali.org/docs/general-use/xfce-faq/
- Contenedores Docker: https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/
- Qué es Kali: https://www.kali.org/docs/introduction/what-is-kali-linux/
- Autenticación: https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html
- Credential stuffing: https://cheatsheetseries.owasp.org/cheatsheets/Credential_Stuffing_Prevention_Cheat_Sheet.html
- Sesiones: https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html
- Recuperación: https://cheatsheetseries.owasp.org/cheatsheets/Forgot_Password_Cheat_Sheet.html
- MFA: https://cheatsheetseries.owasp.org/cheatsheets/Multifactor_Authentication_Cheat_Sheet.html

## Verificación de esta entrega

Compilación de producción y 31 pruebas automatizadas aprobadas de los cinco recorridos, terminal, archivos, instalación, ventanas, evaluación, persistencia, cambio de estudiante, importación, promedio y generación de PDF. Se conserva el generador PDF de la versión anterior. La revisión visual en navegador no se pudo completar porque el navegador de pruebas no respondió; la posición de las ventanas y su adaptación a cada tamaño no han sido comprobadas visualmente en ese entorno.

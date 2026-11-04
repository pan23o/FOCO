# FOCO · Estudia y aprueba

Web de estudio con lectura cómoda de los temas subidos, tutor de dudas y generación de preguntas con IA. El contenido del tema es la única fuente de las respuestas y las preguntas.

## Publicar en Vercel

1. Sube únicamente el contenido de esta carpeta a un repositorio propio llamado `foco`.
2. Importa ese repositorio en Vercel, con la raíz del proyecto en esta carpeta y sin comando de compilación.
3. Activa AI Gateway/OIDC en el proyecto. La función usa `VERCEL_OIDC_TOKEN` en el servidor; como alternativa, configura `AI_GATEWAY_API_KEY` como variable secreta de Vercel. No pongas claves en `index.html`.
4. Despliega el proyecto.

`AI_GATEWAY_MODEL` permite cambiar el modelo; el predeterminado está definido en `api/foco.js`. `vercel.json` permite que la respuesta de IA en streaming tarde hasta 60 segundos.

## Datos y privacidad

Los temas, el progreso y las preguntas se guardan en el almacenamiento local del navegador. No se incluyen en este repositorio ni se envían a Vercel al desplegar. Al pulsar el botón de IA, el tema se envía a la función `/api/foco` y de ahí a Vercel AI Gateway para procesarlo; la función no guarda el contenido en una base de datos.

La copia local `file://` y la web publicada tienen almacenamientos separados. Para llevar los temas existentes a la web, descarga una copia de seguridad desde la copia local y restáurala desde la sección Datos de la web.

# FOCO · Estudia y aprueba

Web de estudio con lectura cómoda de los temas subidos, tutor de dudas y generación de preguntas con IA. El contenido del tema es la única fuente de las respuestas y las preguntas.

## Publicar en Vercel

1. Importa el repositorio `pan23o/FOCO` en Vercel, con la raíz del proyecto en esta carpeta y sin comando de compilación.
2. Entra en [Google AI Studio](https://aistudio.google.com/apikey) y crea una API key gratuita.
3. En Vercel, abre el proyecto `foco` → **Settings → Environment Variables**.
4. Añade `GEMINI_API_KEY` con la clave de AI Studio y selecciona **Production**. Para mantener el uso gratuito, no vincules una cuenta de facturación ni actives un plan de pago.
5. Crea un nuevo despliegue de Production para que la función reciba la variable.

FOCO usa `gemini-3.8-flash` como proveedor principal mediante streaming, con razonamiento de nivel bajo para reducir latencia y consumo. Si todavía no hay una clave Gemini configurada, conserva Groq como respaldo mediante `GROQ_API_KEY`. Cuando existe `GEMINI_API_KEY`, Gemini tiene prioridad.

Los límites del nivel gratuito dependen del proyecto y del modelo. Se pueden consultar en la página **Rate limits** de Google AI Studio. Un error HTTP 429 puede deberse al límite de solicitudes por minuto, tokens o cuota del proyecto; FOCO muestra el detalle que devuelva el proveedor en lugar de asumir que se agotó la cuota diaria.

## Datos y privacidad

Los temas, el progreso y las preguntas se guardan en el almacenamiento local del navegador. No se incluyen en este repositorio ni se envían a Vercel al desplegar. Al pulsar el botón de IA, el tema se envía a la función `/api/foco` y desde ahí al proveedor configurado para procesarlo; la función no guarda el contenido en una base de datos.

Importante: en el nivel gratuito de Gemini, Google indica que el contenido enviado puede utilizarse para mejorar sus productos. No envíes información sensible si usas ese nivel. Consulta las condiciones de Google antes de usar FOCO con materiales privados.

La copia local `file://` y la web publicada tienen almacenamientos separados. Para llevar los temas existentes a la web, descarga una copia de seguridad desde la copia local y restáurala desde la sección Datos de la web.

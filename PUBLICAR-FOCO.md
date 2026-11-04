# Publicar FOCO en GitHub y Vercel

Este paquete contiene solo la aplicación: no incluye tus temas, preguntas ni progreso guardados en el navegador.

## 1. Crear el repositorio en GitHub

1. Entra en [github.com/new](https://github.com/new) con tu cuenta `pan23o`.
2. Pon `FOCO` como nombre y elige **Private**.
3. No marques las opciones para añadir README, `.gitignore` o licencia; el paquete ya las incluye.
4. Pulsa **Create repository**.

## 2. Subir el paquete

1. Descarga `FOCO-web-para-publicar.zip` y extráelo en una carpeta.
2. Abre esa carpeta en el Explorador de Windows.
3. En la barra de dirección escribe `powershell` y pulsa Enter.
4. Copia y ejecuta estas líneas, una por una:

```powershell
git init
git add .
git commit -m "Publica FOCO"
git branch -M main
git remote add origin https://github.com/pan23o/FOCO.git
git push -u origin main
```

Si GitHub abre el navegador para iniciar sesión, autoriza la subida. Cuando termine, los archivos aparecerán en el repositorio `pan23o/FOCO`.

## 3. Crear la web en Vercel

1. Entra en Vercel y pulsa **Add New… → Project**.
2. Importa `pan23o/FOCO`.
3. Pon el nombre del proyecto `foco`, deja la raíz del repositorio y elige **Other** si pregunta por el framework. No hace falta comando de compilación.
4. Pulsa **Deploy**. Vercel publicará la página y `/api/foco`.

## 4. Activar la IA gratuita

1. Entra en [Google AI Studio](https://aistudio.google.com/apikey) y crea una API key.
2. En Vercel abre el proyecto `foco` → **Settings → Environment Variables**.
3. Crea la variable `GEMINI_API_KEY`, pega la clave como valor y marca **Production**.
4. Para mantener el uso en el nivel gratuito, no vincules una cuenta de facturación ni contrates un plan de pago.
5. Después, crea un nuevo despliegue de Production. Las variables nuevas no se aplican a despliegues que ya estaban creados.

FOCO usa Gemini 3.8 Flash como IA principal. Groq queda como respaldo temporal mientras no exista `GEMINI_API_KEY`. Los límites gratuitos de Google dependen del proyecto y se consultan en AI Studio; pueden limitar solicitudes por minuto o tokens. En el nivel gratuito, Google puede utilizar el contenido enviado para mejorar sus productos, así que no envíes datos sensibles.

Nunca pongas la clave en `index.html`, ni la compartas por chat, ni la subas a GitHub.

## 5. Llevar tus temas guardados a la web

La copia local abierta como archivo y la web tienen almacenamientos separados. En la copia local, descarga una copia de seguridad desde **Temas → Datos**. Cuando FOCO esté en la web, usa **Restaurar copia** allí. La copia de seguridad no está incluida en el ZIP ni se sube a GitHub.
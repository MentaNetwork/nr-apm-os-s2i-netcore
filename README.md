# New Relic APM en .Net Core con OpenShift Source2Image

## Componentes

- `app/`<br>
  Es una aplicación .Net de ejemplo, que tiene en el directorio `.s2i/` una configuración especial de Source2Image para instalar New Relic APM.
- `.s2i/`<br>
  El directorio [.s2i](app/.s2i) se puede copiar y pegar en cualquier otra aplicación, dentro del directorio `contextDir` especificado en el `BuildConfig`.
- `.s2i/environment`<br>
  El archivo [.s2i/environment](app/.s2i/environment) contiene la *configuración* del agente APM.
- `.s2i/bin/assemble`<br>
  El archivo [.s2i/bin/assemble](app/.s2i/bin/assemble) contiene los *comandos de instalación* del agente APM.


## Instrucciones

Instrucciones para instalar New Relic APM en una app .Net tomando este repositorio como ejemplo:

1. Copiar el directorio [.s2i](app/.s2i) en el `contextDir` del `BuildConfig` de la app.
2. Definir la configuración del agente New Relic APM en el archivo [.s2i/environment](app/.s2i/environment).
   1. `NEW_RELIC_APP_NAME` es el nombre de la aplicación tal cual la queramos ver reportada en New Relic One.
   2. `NEW_RELIC_LICENSE_KEY` es la llave de licencia de la cuenta de New Relic One.
3. Generar un nuevo build en OpenShift y desplegarlo.
4. Generar un poco de actividad en el pod y esperar un minuto a que se reporte en New Relic One.


*Nota:* las variables de entorno `NEW_RELIC_*` pueden definirse en [.s2i/environment](app/.s2i/environment) o en la configuración de entorno del `BuildConfig`, donde se podrán personalizar más fácilmente de acuerdo al entorno (prod, stage, dev, etc).
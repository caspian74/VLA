# Los Alazanes, Granero y Veterinaria

Sitio estático (HTML, CSS y JS, sin build ni dependencias). Todo el sitio vive en `public/`.

```
public/
  index.html      página completa
  images/         equipo.jpg, fachada.jpg
  logo.svg        logo en vector
  favicon.svg
  _headers        cabeceras de seguridad y caché
  robots.txt
wrangler.jsonc    configuración para Cloudflare Workers
```

## Antes de publicar: datos pendientes

Busca `EDITAR` en `public/index.html`:

1. **Dirección**: sustituir `Av. Ejemplo 123, Col. Centro`.
2. **Horario**: cambiar la tabla de la sección "Visítanos" y el objeto `H` del script (el aviso "Abierto ahora" lo usa).
3. **WhatsApp**: el número `5216646880210` (formato `521` + 10 dígitos) aparece en el botón flotante y en el script (`var WA`). Confirma que ese número recibe WhatsApp.
4. **Reseñas**: son de ejemplo; cámbialas por reales.
5. Opcional: agregar `<meta property="og:image">` con la URL absoluta de una imagen cuando ya tengas dominio.

## Desplegar en Cloudflare Workers (recomendado)

1. Sube este repo a GitHub.
2. Cloudflare Dashboard > Workers & Pages > Create > Import a repository.
3. Selecciona el repo. Build command: vacío. Deploy command: `npx wrangler deploy`.
4. Deploy. El nombre del proyecto debe coincidir con `name` en `wrangler.jsonc`.

Desde la terminal: `npx wrangler deploy`.

## Desplegar en Cloudflare Pages

1. Workers & Pages > Create > Pages > Connect to Git.
2. Framework preset: None. Build command: vacío. **Build output directory: `public`**.
3. Save and Deploy.

## Dominio propio

En el proyecto: Settings > Domains & Routes (Workers) o Custom domains (Pages).

## Vista local

`npx serve public` o abrir `public/index.html` en el navegador.

## Si el deploy falla con "Could not detect a directory containing static files"

`wrangler.jsonc` y la carpeta `public/` deben estar en la **raíz del repositorio** (no dentro de otra carpeta). Si quedaron dentro de una subcarpeta, mueve todo a la raíz, o en Cloudflare ve a Settings > Build > Root directory y escribe el nombre de esa subcarpeta.

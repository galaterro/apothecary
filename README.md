# Apothecary · web de enlaces

Página de enlaces de **Apothecary** (temas propios desde Alcorcón), tipo Linktree pero nuestra.
Está pensada sobre todo para móvil y se publica gratis con GitHub Pages.

Dirección de la web: **https://galaterro.github.io/apothecary/**

---

## ✏️ Cambiar los enlaces (no hace falta saber programar)

Todo lo que sale en la web está en un solo archivo: **[`_data/enlaces.yml`](_data/enlaces.yml)**.

1. Entra en el repositorio en github.com (vale desde el móvil, con el navegador).
2. Abre la carpeta `_data` y el archivo `enlaces.yml`.
3. Pulsa el lápiz ✏️ (*Edit this file*).
4. Cambia lo que quieras. Al principio del archivo hay instrucciones y ejemplos listos
   para usar (Instagram, Spotify, TikTok, un concierto, contacto...).
5. Pulsa **Commit changes** (y otra vez *Commit changes* en la ventana que sale).

En 1-2 minutos la web está actualizada. Si no ves el cambio, recarga la página
(a veces el móvil guarda la versión anterior un rato).

Un enlace se escribe así:

```yaml
  - titulo: Spotify
    url: https://open.spotify.com/artist/...
```

Opcionalmente se le puede añadir `subtitulo:` (texto pequeño debajo), `destacado: true`
(botón resaltado, para un estreno o un concierto) e `icono:`. El icono normalmente
no hace falta: se pone solo según la web del enlace.

**¿Y si me equivoco?** Si el archivo queda mal escrito (por ejemplo, una sangría
descolocada), GitHub no publica el cambio y la web sigue como estaba. En la pestaña
**Actions** del repositorio aparece una ❌ roja; basta con corregir el archivo y guardar
de nuevo. También se puede volver a una versión anterior desde el historial del archivo
(botón *History*).

## 👥 Dar permiso a otra persona para editar

El dueño del repositorio entra en **Settings → Collaborators → Add people** y añade
la cuenta de GitHub de quien vaya a editar (tiene que hacerse una cuenta gratis).
Le llega una invitación por correo; al aceptarla ya puede seguir los pasos de arriba.

## 🚀 Publicar la web (solo la primera vez)

1. El repositorio tiene que ser **público** (con el plan gratuito de GitHub).
2. **Settings → Pages**.
3. En *Build and deployment*, *Source*: **Deploy from a branch**.
4. *Branch*: la rama principal (`main`) y la carpeta **`/ (root)`** → **Save**.
5. A los pocos minutos aparece arriba el enlace a la web.

Si algún día compráis un dominio (por ejemplo `apothecary.es`), se configura en esa
misma pantalla, en *Custom domain*; no hay que tocar nada más de la web.

## 🗂️ Qué hay en cada sitio

| Archivo | Para qué sirve |
| --- | --- |
| `_data/enlaces.yml` | **Los enlaces y la frase de debajo del logo.** Lo único que hay que tocar normalmente. |
| `_config.yml` | Nombre y descripción de la web (lo que sale en Google y al compartir). |
| `assets/img/` | Logo, icono de la pestaña y la imagen que sale al compartir el enlace por WhatsApp o redes (`og.jpg`). |
| `assets/css/estilo.css` | Diseño. Los colores están arriba del todo, en `:root`. |
| `index.html` | Estructura de la página. |
| `_includes/enlace.html` | Cómo se pinta cada botón y cómo se elige el icono. |
| `_data/iconos.yml` | Los iconos de cada plataforma. |

## 💻 Verla en tu ordenador (opcional)

Solo si quieres probar cambios de diseño antes de subirlos. Con Ruby instalado:

```sh
gem install jekyll
jekyll serve
```

y abre http://localhost:4000

## Créditos

- Logo: Apothecary.
- Tipografía: [IM Fell](https://iginomarini.com/fell/) de Igino Marini (licencia SIL OFL, ver `assets/fonts/OFL.txt`).
- Iconos de marcas: [Simple Icons](https://simpleicons.org) (CC0). Iconos genéricos: [Lucide](https://lucide.dev) (ISC).

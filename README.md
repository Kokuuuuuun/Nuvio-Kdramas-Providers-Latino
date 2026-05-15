# Nuvio Latino Hub Providers

Scrapers para Nuvio Media Hub con contenido en Español Latino (Cine, Series, Anime y Doramas).

---

## ✅ Providers Activos

### 🎬 Vimeus (`vimeus.com`) - **All-in-One**
- **Estado:** ✅ Funcional
- **Contenido:** Películas, Series y Anime (Todo en uno)
- **Idioma:** Español Latino
- **Resolvers:** VOE, GoodStream, Vimeos, VidHide/Do7Go, OkRu, Filemoon
- **Integración:** Embed directo vía API oficial (TMDB ID)
- **Versión:** 1.0.0

### 🎭 DoramasFlix (`doramasflix.in`) - **Especializado**
- **Estado:** ✅ Funcional
- **Contenido:** Doramas Coreanos, Chinos, Japoneses y Asiáticos
- **Idioma:** Español / Latino
- **Resolvers:** VOE, StreamWish, VidHide/Do7Go, OkRu, Filemoon
- **Versión:** 1.2.0

---

## 🚀 Cargar en Nuvio

Añade esta URL en **Nuvio → Settings → Plugins:**

```
https://raw.githubusercontent.com/Kokuuuuuun/Nuvio-Kdramas-Providers-Latino/main/manifest.json
```
*(Nota: Cambia el nombre del repo en la URL si decides renombrarlo en GitHub)*

---

## 🛠️ Capacidades de Extracción

### Servidores Soportados
| Servidor | Estado | Nota |
|---|---|---|
| **VOE** | ✅ OK | Bypass de tokens y loaders JS |
| **Vimeos** | ✅ OK | Unpacker de 343 símbolos |
| **GoodStream** | ✅ OK | Extracción directa de m3u8 |
| **OkRu** | ✅ OK | Selección de calidad automática |
| **VidHide / DS2Play** | ✅ OK | Desempaquetado de JS eval |
| **Filemoon** | ✅ OK | Búsqueda dinámica de fuentes |
| **StreamWish** | ⚠️ Proxy | Requiere headers específicos |

---

## 📁 Estructura del Proyecto

```
src/
├── vimeus/              # Provider Multi-contenido
└── doramasflix/         # Provider Especializado en Doramas
providers/
├── vimeus.js            # Bundle compilado
└── doramasflix.js       # Bundle compilado
```

---

## 🔨 Desarrollo y Build

```bash
# Construir todos los plugins
node build.js

# Testear Vimeus (Ejemplo: Fight Club)
node test-vimeus.js movie 550
```

---

## 🗺️ Roadmap

- [ ] **Bypass Cloudflare** - Para servidores como HlsWish
- [ ] **DoramasVIP** - Próxima integración
- [ ] **Personalización de Calidad** - Selector manual en Nuvio

# Política de Privacidad / Privacy Policy — Watchlist+

*Última actualización / Last updated: Octubre 2026 (Versión 1.1.4)*

---

## 🇪🇸 Español (Spanish)

### Introducción y Filosofía "Privacy-First"
**Watchlist+** es una extensión de navegador de código abierto diseñada para registrar, organizar y llevar el seguimiento del progreso de visualización de series, anime y películas en cualquier sitio web de forma local y privada.

Nuestra filosofía fundamental es que **tus datos te pertenecen exclusivamente a ti**. Watchlist+ opera bajo una arquitectura de almacenamiento local preferente (*Local-First*). Esta Política de Privacidad describe de manera transparente y detallada nuestras prácticas con respecto a la **recopilación, manipulación, almacenamiento y uso compartido** de los datos del usuario, de conformidad estricta con las Políticas del Programa para Desarrolladores de Chrome Web Store.

---

### 1. Recopilación de Datos del Usuario (Data Collection)
Watchlist+ recopila y procesa únicamente la información estrictamente necesaria para brindar sus funcionalidades de seguimiento:

1. **Datos generados directamente por el usuario:**
   - Títulos de series, animes, películas y páginas web agregadas a la colección.
   - Conteo de capítulos vistos, total de episodios y estado de visualización (*viendo*, *terminada*, *pausada*, *abandonada*, *por ver*).
   - Conjuntos (carpetas), separadores visuales, fechas de estreno, valoraciones personales y notas personalizadas.
   - Nombres y fotos de avatar de perfiles locales creados en la extensión.
   - Preferencias de interfaz (tema visual, fondo personalizado, configuración de carátulas).

2. **Datos de pestañas y navegación (Pestaña Activa):**
   - Cuando el usuario navega en sitios web o reproductores de video compatibles, el script de contenido (`content.js`) inspecciona el título de la página web (`document.title`) y la URL actual de la pestaña activa con el único propósito de identificar si coincide con una serie guardada y extraer el número de capítulo actual.
   - **Alcance limitado:** Esta lectura opera exclusivamente en la pestaña que el usuario está visualizando activamente. No se registra un historial general de navegación.

3. **Datos de identidad y autenticación (OAuth 2.0 — Opcional):**
   - Si el usuario decide activar voluntariamente la sincronización con Google Drive o validar su suscripción PRO, la extensión solicita acceso mediante `chrome.identity`.
   - Se procesa la dirección de correo electrónico asociada a la cuenta de Google del usuario para identificar la cuenta y autenticar las copias de seguridad.

4. **Claves de API y credenciales provistas por el usuario (Opcional):**
   - Si el usuario decide utilizar las funciones de Inteligencia Artificial (asistente Kuro-Byte, recomendaciones y resúmenes anti-spoilers), puede ingresar su propia clave de API gratuita de Google AI Studio (Gemini). Dicha clave se guarda exclusivamente en el almacenamiento local del navegador del usuario.

5. **Datos que Watchlist+ NUNCA recopila:**
   - **NO** recopilamos contraseñas ni datos bancarios.
   - **NO** recopilamos historiales completos de navegación ni historiales de búsqueda.
   - **NO** recopilamos direcciones IP, geolocalización física ni huellas digitales del dispositivo (*device fingerprinting*).
   - **NO** recopilamos contenido multimedia ni grabamos transmisiones de video.

---

### 2. Manipulación y Uso de los Datos (Data Handling and Use)
Los datos recopilados se manipulan y utilizan exclusivamente para los siguientes propósitos operativos:

1. **Detección automática y actualización del progreso:**
   - La URL y el título de la página del video se analizan en la memoria local del navegador mediante patrones de expresiones regulares para detectar expresiones como *"Episodio 12"* o *"Capítulo 5"*. Si hay coincidencia, se actualiza el contador de episodios vistos en la biblioteca local del usuario.

2. **Organización, búsqueda y visualización:**
   - Los títulos y metadatos guardados se indexan localmente para permitir filtrado por categorías, búsqueda instantánea por texto, cálculo de estadísticas de tiempo invertido y generación de calendarios de emisión semanales.

3. **Sincronización de respaldos en la nube (Google Drive — Opcional):**
   - Cuando el usuario inicia una copia de seguridad, la extensión empaqueta la biblioteca en formato JSON (`profile_${id}.json`) y la transfiere directamente a la carpeta privada de aplicación del usuario en Google Drive (`drive.appdata`).

4. **Validación de licencias PRO y notificaciones de Telegram (Opcional):**
   - Para verificar suscripciones PRO adquiridas mediante Ko-fi, se envía el correo electrónico del usuario mediante HTTPS a un endpoint de Google Apps Script gestionado por el desarrollador para contrastar la licencia.
   - Para las alertas móviles de Telegram (opcional), se envía un identificador pseudoanónimo de chat y la lista de títulos seguidos para programar el envío de alertas de estreno.

5. **Consultas a Inteligencia Artificial (Google Gemini — Opcional):**
   - Si el usuario solicita una recomendación o resumen anti-spoilers, se envía el prompt y únicamente los títulos relevantes de su biblioteca directamente a los servidores oficiales de Google AI (`generativelanguage.googleapis.com`) usando la clave del usuario. No se transmiten datos personales identificables.

6. **Consultas a metadatos públicos de sólo lectura (AniList, TVmaze, Wikipedia):**
   - La extensión envía consultas de texto anónimas con el nombre de la serie a APIs públicas para obtener carátulas oficiales, días de emisión y traducción de títulos internacionales. Estas consultas no envían datos del usuario.

---

### 3. Almacenamiento, Retención y Seguridad de los Datos (Data Storage, Retention, and Security)

1. **Almacenamiento Local (Local-First):**
   - Todos los datos de la biblioteca, historial de episodios y configuraciones se almacenan directamente en el equipo del usuario a través de la API estándar `chrome.storage.local`.
   - Este almacenamiento se encuentra aislado dentro del sandbox de extensiones del navegador y está protegido por los mecanismos de seguridad nativos de Chromium / Chrome.

2. **Almacenamiento en la Nube (Google Drive):**
   - Los respaldos en la nube se almacenan exclusivamente en el espacio `drive.appdata` de la cuenta de Google del usuario. Esta área es privada y oculta: ningún tercero ni ninguna otra aplicación de Google Drive tiene acceso a dichos archivos, excepto Watchlist+.

3. **Período de Retención:**
   - Los datos locales se conservan indefinidamente en el dispositivo del usuario mientras la extensión esté instalada, garantizando la persistencia de su historial de visualización.
   - Si el usuario desinstala la extensión o borra los datos de navegación, todos los datos locales almacenados en `chrome.storage.local` se eliminan de manera permanente e irrecuperable de forma inmediata.

4. **Medidas de Seguridad:**
   - Todas las comunicaciones con servicios externos (Google Drive, Google AI Studio, Google Apps Script, AniList, TVmaze, Wikipedia) se realizan a través de canales cifrados mediante protocolo HTTPS / TLS 1.3.
   - No se almacenan credenciales ni contraseñas en texto plano. Los tokens OAuth se gestionan de forma segura a través del subsistema `chrome.identity`.

---

### 4. Uso Compartido y Divulgación a Terceros (Data Sharing and Third-Party Disclosure)

1. **Compromiso Estricto de No Venta ni Comercialización:**
   - **Watchlist+ NO vende, NO alquila, NO comercializa ni transfiere datos personales, historial de navegación o información del usuario a corredores de datos (*data brokers*), redes publicitarias, empresas de análisis de mercado ni anunciantes.**
   - **Los datos del usuario NUNCA se utilizan con fines de segmentación publicitaria, calificación crediticia o telemetría invasiva.**

2. **Divulgaciones a Proveedores de Servicios Autorizados:**
   La extensión únicamente transfiere información técnica hacia servicios de terceros indispensables cuando el usuario invoca explícitamente las siguientes funcionalidades:

   | Destinatario / Servicio | Tipo de Dato Transferido | Propósito Exclusivo |
   | :--- | :--- | :--- |
   | **Google Drive API** (`googleapis.com`) | Archivo de respaldo JSON con la biblioteca del usuario | Guardar y restaurar copias de seguridad en la nube privada del propio usuario. |
   | **Google Apps Script** (`script.google.com`) | Dirección de correo electrónico de Google del usuario | Validar la validez de licencias del plan PRO adquiridas por el usuario. |
   | **Google Generative Language API** (`generativelanguage.googleapis.com`) | Texto de consulta y títulos de series seleccionados | Generar recomendaciones y resúmenes sin spoilers mediante la clave provista por el usuario. |
   | **AniList GraphQL API** (`graphql.anilist.co`) | Título público de anime consultado | Obtener fecha y hora de emisión y metadatos oficiales (consulta anónima de sólo lectura). |
   | **TVmaze REST API** (`api.tvmaze.com`) | Título público de serie de TV consultado | Obtener calendario de emisión y cadenas televisivas (consulta anónima de sólo lectura). |
   | **Wikipedia API** (`es.wikipedia.org`) | Título de la obra en español | Obtener el título canónico en inglés mediante enlace inter-idioma (consulta anónima de sólo lectura). |
   | **Telegram Bot API** (`api.telegram.org`) | ID de chat de Telegram y mensaje de texto | Enviar avisos de nuevos episodios estrenados si el usuario vinculó su cuenta. |

---

### 5. Derechos del Usuario y Eliminación de Datos (User Rights and Data Deletion)
En cumplimiento de las normativas de privacidad globales (GDPR, CCPA) y las directivas de Chrome Web Store, todo usuario de Watchlist+ tiene control absoluto sobre sus datos:

1. **Derecho de Acceso y Portabilidad:**
   - El usuario puede descargar en cualquier momento una copia íntegra de todos sus datos almacenados en formato estándar `.json` haciendo clic en el botón **"Exportar"** dentro de la biblioteca.

2. **Derecho de Supresión y Eliminación Total:**
   - **Eliminación local:** El usuario puede eliminar todos sus datos locales en cualquier momento desde los Ajustes de la extensión haciendo clic en *"Eliminar todos los datos"* o simplemente desinstalando Watchlist+ de su navegador (lo que elimina el 100% de `chrome.storage.local`).
   - **Eliminación en la nube:** El usuario puede eliminar sus copias de seguridad de Google Drive en cualquier momento desde el menú de sincronización de la extensión, o desde `https://drive.google.com` ingresando en *Configuración → Administrar aplicaciones → Watchlist+ → Eliminar datos de aplicación ocultos*.

3. **Revocación de Permisos de Autenticación:**
   - El usuario puede revocar el acceso de Watchlist+ a su cuenta de Google en cualquier momento ingresando en la página oficial de seguridad de Google: `https://myaccount.google.com/permissions`.

---

### 6. Permisos del Navegador y Justificación Detallada (Permissions Justification)
Watchlist+ aplica el principio de privilegios mínimos. A continuación se justifica cada permiso solicitado en `manifest.json`:

| Permiso | Propósito Técnico y Justificación |
| :--- | :--- |
| `storage` / `unlimitedStorage` | Permite guardar localmente tu biblioteca, listas de capítulos, notas y configuraciones dentro del navegador del usuario sin bloqueos de cuota de disco. |
| `tabs` / `activeTab` | Permite leer la URL y el título de la pestaña activa en sitios de reproducción de video para reconocer el episodio y actualizar el contador de forma automática. No supervisa pestañas no activas ni registra navegación general. |
| `notifications` | Permite emitir notificaciones locales del sistema cuando se confirma el respaldo automático o cuando se estrena un capítulo programado en el calendario. |
| `alarms` | Permite programar de forma eficiente la ejecución periódica de los respaldos automáticos y la comprobación de estrenos sin gastar recursos de CPU continuamente. |
| `downloads` | Permite descargar los archivos de respaldo `.json` directamente en la carpeta de Descargas del usuario al pulsar "Exportar". |
| `identity` | Utilizado exclusivamente para iniciar el flujo seguro de autenticación OAuth 2.0 con Google para sincronización con Google Drive y comprobación de licencias PRO. |
| `host_permissions` (`<all_urls>`) | Necesario para inyectar el script de detección (`content.js`) en reproductores y portales de video abiertos de cualquier dominio web, permitiendo detectar series sin restringirse a sitios predefinidos. No se recopilan datos de páginas que no reproduzcan video. |

---

### 7. Privacidad de Menores
Watchlist+ no está dirigida a menores de 13 años y no recopila a sabiendas ningún tipo de información identificable de niños. Si un padre o tutor tiene conocimiento de que sus datos fueron provistos, puede solicitar su eliminación inmediata contactándonos.

---

### 8. Contacto
Para cualquier duda, solicitud de derechos de privacidad o consulta sobre el tratamiento de datos, puedes comunicarte a través de:
- **Repositorio oficial de soporte:** [https://github.com/LisandroUr/watchlist-policy](https://github.com/LisandroUr/watchlist-policy)
- **Contacto del Desarrollador:** A través de la página oficial de soporte en la Chrome Web Store.

---
---

## 🇬🇧 English

### Overview & "Privacy-First" Philosophy
**Watchlist+** is an open-source browser extension designed to track, organize, and manage watch progress for series, anime, and movies across any website locally and privately.

Our core principle is simple: **your data belongs exclusively to you**. Watchlist+ operates under a strict *Local-First* architecture. This Privacy Policy comprehensively and transparently discloses our practices regarding the **collection, handling, storage, and sharing** of user data, fully compliant with the Chrome Web Store Developer Program Policies.

---

### 1. User Data Collection
Watchlist+ collects and handles only the data strictly required to deliver its core tracking and organization features:

1. **Direct User-Generated Data:**
   - Titles of series, anime, movies, and custom web pages saved to your collection.
   - Watched episode counts, total episode numbers, and watch status (*watching*, *completed*, *on-hold*, *dropped*, *plan-to-watch*).
   - Folder sets, separators, release schedules, personal ratings, and custom notes.
   - User profile names and local avatar images.
   - Interface preferences (theme colors, custom wallpapers, cover layout choices).

2. **Active Tab & Browsing Data:**
   - While the user actively watches video content on streaming platforms, the content script (`content.js`) inspects the current active tab's page title (`document.title`) and current page URL solely to detect matches against tracked titles and parse the episode number.
   - **Strictly Limited Scope:** Only the currently active foreground tab is inspected. General browsing history is never recorded, captured, or transmitted.

3. **Authentication & Identity Data (OAuth 2.0 — Optional):**
   - If the user voluntarily enables Google Drive sync or verifies their PRO subscription, the extension requests authorization through `chrome.identity`.
   - The user's Google account email address is processed to authenticate the session and verify cloud backups.

4. **User-Provided API Keys & Credentials (Optional):**
   - If the user enables optional AI features (Kuro-Byte AI assistant, smart recommendations, and spoiler-free recaps), they may provide their own free Google AI Studio (Gemini) API key. This key is stored strictly within the user's local browser storage.

5. **Data Watchlist+ NEVER Collects:**
   - We **DO NOT** collect passwords or payment details.
   - We **DO NOT** collect broad browsing history or search history.
   - We **DO NOT** collect IP addresses, physical geolocation, or device fingerprints.
   - We **DO NOT** capture media content or record streaming video streams.

---

### 2. Data Handling and Usage
All data handled by Watchlist+ is processed exclusively for the following functional purposes:

1. **Automated Progress Tracking:**
   - Active tab URLs and page titles are evaluated locally in memory using regular expressions to extract terms like *"Episode 12"* or *"Chapter 5"*. Upon a match, the episode count is updated in the user's local library.

2. **Library Organization, Search, and Analytics:**
   - Saved titles and metadata are indexed locally to provide instant search filtering, watch time statistics, and weekly release calendar schedules.

3. **Cloud Backup Synchronization (Google Drive — Optional):**
   - When the user initiates a backup, the library data is packaged into JSON format (`profile_${id}.json`) and transmitted directly to the user's private Google Drive application folder (`drive.appdata`).

4. **PRO License Verification & Telegram Alerts (Optional):**
   - For users with a PRO license purchased via Ko-fi, the user's email address is transmitted over HTTPS to a Google Apps Script endpoint operated by the developer to verify active license status.
   - For optional Telegram mobile alerts, a pseudo-anonymous chat ID and airing watchlist are synced to deliver release notifications.

5. **AI Assistant Processing (Google Gemini — Optional):**
   - When the user requests a recommendation or recap, the user prompt and relevant library titles are sent directly to official Google AI servers (`generativelanguage.googleapis.com`) using the user's API key. No personal identity data is attached.

6. **Public Metadata Queries (AniList, TVmaze, Wikipedia):**
   - The extension sends anonymous, read-only text queries to public APIs to retrieve official cover artwork, broadcast air times, and international title translations. No user data is transmitted during these requests.

---

### 3. Data Storage, Retention, and Security

1. **Local-First Storage:**
   - All library records, episode progress, and configurations reside directly on the user's local machine via the standard `chrome.storage.local` API.
   - This storage is isolated within the browser's extension sandbox and protected by Chromium's native security policies.

2. **Cloud Storage (Google Drive):**
   - Cloud backups reside solely in the user's personal Google Drive `drive.appdata` space. This area is completely private: no third parties or other Google Drive apps can view or access these files.

3. **Retention Duration:**
   - Local data is retained on the user's device for as long as the extension remains installed.
   - If the user uninstalls the extension or clears their browser storage, all local data stored in `chrome.storage.local` is immediately, permanently, and irrevocably deleted.

4. **Security Measures:**
   - All external transmissions (Google Drive, Google AI Studio, Google Apps Script, AniList, TVmaze, Wikipedia) occur exclusively over encrypted HTTPS / TLS 1.3 connections.
   - No plaintext passwords or credentials are stored. OAuth tokens are managed securely through the browser's native `chrome.identity` API.

---

### 4. Data Sharing and Third-Party Disclosure

1. **Strict No-Sale Commitment:**
   - **Watchlist+ DOES NOT sell, rent, lease, monetize, or transfer personal data, browsing history, or user records to data brokers, ad networks, analytics firms, or marketing companies.**
   - **User data is NEVER used for targeted advertising, credit assessment, or commercial telemetry.**

2. **Authorized Third-Party Service Providers:**
   The extension only communicates with third-party service providers when the user explicitly triggers features that require them:

   | Provider / Service | Data Transmitted | Specific Purpose |
   | :--- | :--- | :--- |
   | **Google Drive API** (`googleapis.com`) | JSON library backup file | Storing and restoring backups in the user's private cloud storage. |
   | **Google Apps Script** (`script.google.com`) | User's Google account email address | Verifying active PRO license status. |
   | **Google Generative Language API** (`generativelanguage.googleapis.com`) | Search prompt and relevant library titles | Generating AI recommendations and summaries using the user's API key. |
   | **AniList GraphQL API** (`graphql.anilist.co`) | Anime title query | Retrieving official airing schedules and genres (anonymous, read-only). |
   | **TVmaze REST API** (`api.tvmaze.com`) | TV series title query | Retrieving airing schedules and network info (anonymous, read-only). |
   | **Wikipedia API** (`es.wikipedia.org`) | Localized title string | Translating localized titles to canonical international titles (anonymous, read-only). |
   | **Telegram Bot API** (`api.telegram.org`) | Telegram chat ID and alert message | Delivering episode release notifications if linked by the user. |

---

### 5. User Rights and Data Deletion
In accordance with global privacy frameworks (GDPR, CCPA) and Chrome Web Store policies, users retain complete sovereignty over their data:

1. **Right to Access & Portability:**
   - Users can export a complete, unencrypted copy of all their data in standard `.json` format at any time by clicking **"Exportar" / "Export"** in the library.

2. **Right to Erasure & Complete Deletion:**
   - **Local Deletion:** Users can delete all local data at any time via Settings (*"Eliminar todos los datos"*) or by simply uninstalling Watchlist+ from their browser (instantly purging 100% of `chrome.storage.local`).
   - **Cloud Deletion:** Users can delete cloud backups at any time through the extension interface or directly via `https://drive.google.com` under *Settings → Manage Apps → Watchlist+ → Delete hidden app data*.

3. **Revocation of Permissions:**
   - Users can revoke Google account access at any time by visiting Google's official permissions manager: `https://myaccount.google.com/permissions`.

---

### 6. Browser Permissions & Justification
Watchlist+ adheres to the principle of least privilege. Every permission in `manifest.json` is justified below:

| Permission | Technical Purpose & Justification |
| :--- | :--- |
| `storage` / `unlimitedStorage` | Stores watchlist entries, episode counters, notes, and preferences locally in the browser without storage quota limits. |
| `tabs` / `activeTab` | Inspects the active tab's URL and title on video playback websites to automatically identify the show and increment the episode counter. Non-active tabs are never read. |
| `notifications` | Displays local desktop notifications for automated backup completions and scheduled release reminders. |
| `alarms` | Schedules lightweight background routines for automatic backups and release calendar checks without taxing CPU resources. |
| `downloads` | Downloads exported `.json` backup files directly to the user's Downloads directory upon request. |
| `identity` | Initiates secure OAuth 2.0 authentication flows with Google for Google Drive backups and PRO license verification. |
| `host_permissions` (`<all_urls>`) | Injects the detection content script (`content.js`) into open video players across any streaming website, enabling universal show detection without being locked to fixed domains. Pages not playing video are ignored. |

---

### 7. Children's Privacy
Watchlist+ is not directed to children under 13 years of age and does not knowingly collect any personally identifiable information from children. If a parent or guardian becomes aware that their child has provided data, they may contact us for immediate deletion.

---

### 8. Contact Information
For any inquiries, privacy concerns, or data rights requests, please contact us via:
- **Official Support Repository:** [https://github.com/LisandroUr/watchlist-policy](https://github.com/LisandroUr/watchlist-policy)
- **Developer Support:** Via the official Chrome Web Store item support page.

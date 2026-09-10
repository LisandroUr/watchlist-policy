# Política de Privacidad / Privacy Policy — Watchlist+

*Última actualización / Last updated: Septiembre 2026*

---

## Español (Spanish)

### 1. Resumen y Filosofía "Privacy-First"
**Watchlist+** es una extensión de navegador diseñada para organizar y llevar el seguimiento del progreso de visualización de series, anime y películas de forma local.
Nuestra filosofía fundamental es que tus datos te pertenecen exclusivamente a ti. **Watchlist+ no recopila, no transmite, no almacena en servidores externos ni comercializa ningún tipo de información personal, historial de navegación o hábitos de consumo.**

La única excepción es la sincronización opcional con **Google Drive**, que el usuario activa de forma explícita para hacer copias de seguridad de su biblioteca en su propia cuenta de Google.

### 2. Datos Almacenados y Ubicación
Todos los datos generados por el usuario se guardan de forma local en el navegador utilizando la API estándar `chrome.storage.local`:
- Lista de series, películas y páginas guardadas.
- Número de episodios vistos y estado de visualización.
- Conjuntos (carpetas), separadores y notas personalizadas.
- Perfiles de usuario y preferencias estéticas (fondos personalizados, tema claro/oscuro).

**En ningún momento estos datos salen de tu dispositivo sin tu consentimiento explícito.** Si desinstalas la extensión o limpias los datos del navegador, los datos se eliminan a menos que hayas creado un archivo de respaldo manual o activado la sincronización con Google Drive.

### 3. Servicios Externos Utilizados

#### 3a. Google Drive (Sincronización de Respaldos — Opcional)
Si el usuario elige activar la sincronización con Google Drive, la extensión utiliza el permiso `identity` para solicitar un token OAuth 2.0 de Google y acceder **exclusivamente** a los archivos creados por la propia extensión en el Drive del usuario. No se leen, modifican ni eliminan archivos ajenos a Watchlist+. Esta funcionalidad es completamente opcional y puede desactivarse en cualquier momento desde los Ajustes.

#### 3b. Google Apps Script (Validación de Plan PRO — Opcional)
Para los usuarios que adquieren el plan PRO, la extensión consulta un endpoint de Google Apps Script propiedad del desarrollador para verificar el estado de la suscripción. En esta consulta únicamente se envía la dirección de correo electrónico de Google del usuario (obtenida tras su consentimiento mediante OAuth) con el único propósito de confirmar si tiene una licencia PRO activa. **No se almacena ningún otro dato personal en este proceso.**

### 4. Justificación de Permisos Solicitados
Watchlist+ solicita únicamente los permisos estrictamente necesarios para su funcionamiento (principio de privilegios mínimos):

| Permiso | Propósito y Justificación |
| :--- | :--- |
| `storage` / `unlimitedStorage` | Permite guardar tu biblioteca de series, progreso y configuraciones directamente en el almacenamiento interno de tu navegador sin riesgo de saturar cuotas de tamaño al tener bibliotecas grandes. |
| `tabs` / `activeTab` | Permite detectar el título de la serie y el número de episodio en la pestaña activa de las plataformas de streaming compatibles para actualizar tu progreso de forma automática. No registra ni lee datos ajenos a las páginas de video soportadas. |
| `notifications` | Permite mostrar avisos locales sobre estrenos programados de tu calendario o avisarte cuando se ha generado una copia de seguridad automática. |
| `alarms` | Permite programar de forma periódica en segundo plano la rutina de respaldo automático y la verificación de fechas de estreno. |
| `downloads` | Permite descargar en tu carpeta local de "Descargas" el archivo de respaldo `.json` generado al presionar "Exportar" o mediante el backup automático. |
| `identity` | Utilizado exclusivamente para autenticar al usuario con su cuenta de Google mediante OAuth 2.0, con el fin de sincronizar respaldos en Google Drive y verificar el estado del plan PRO. No se accede a ningún otro servicio ni dato de la cuenta. |
| `host_permissions` (sitios de streaming) | La extensión inyecta un script de detección en páginas de sitios de streaming para identificar automáticamente qué serie está reproduciendo el usuario. Solo se lee la URL y el título de la página; no se transmite esta información a ningún servidor externo. |

### 5. Analíticas y Rastreadores de Terceros
Watchlist+ **NO** utiliza:
- Google Analytics u otros rastreadores de telemetría.
- Redes publicitarias (Ad Networks).
- Cookies de seguimiento.
- Servicios de monitoreo de comportamiento.

### 6. Copias de Seguridad y Portabilidad
La extensión incluye una funcionalidad para exportar e importar todos tus datos en un archivo `.json`. La custodia y resguardo de este archivo depende exclusivamente de ti. Opcionalmente, puedes activar la sincronización automática con tu propia cuenta de Google Drive.

### 7. Contacto
Si tienes preguntas o sugerencias respecto a la privacidad de Watchlist+, puedes abrir un issue o enviar un mensaje a través del repositorio del proyecto.

---

## English

### 1. Overview & "Privacy-First" Philosophy
**Watchlist+** is a browser extension created to organize and track anime, series, and movie watch progress locally.
Our core principle is simple: your data belongs exclusively to you. **Watchlist+ does not collect, transmit, store on external servers, or sell any personal information, browsing history, or user habits.**

The only exception is the optional **Google Drive** sync, which users explicitly enable to back up their library to their own Google account.

### 2. Stored Data and Location
All user-generated information is stored locally within your browser using the standard `chrome.storage.local` API:
- List of saved series, movies, and web pages.
- Episode watch progress and status.
- Folder sets, separators, and custom notes.
- User profiles and interface preferences (custom wallpapers, theme colors).

**Your data never leaves your computer without your explicit consent.** If you uninstall the extension or clear your browser data, this information will be permanently deleted unless you exported a backup file or enabled Google Drive sync.

### 3. External Services Used

#### 3a. Google Drive (Backup Sync — Optional)
If the user chooses to enable Google Drive sync, the extension uses the `identity` permission to request a Google OAuth 2.0 token and access **only** the files created by the extension itself in the user's Drive. No files outside of Watchlist+ are ever read, modified, or deleted. This feature is entirely optional and can be disabled at any time in Settings.

#### 3b. Google Apps Script (PRO Plan Validation — Optional)
For users who purchase the PRO plan, the extension queries a Google Apps Script endpoint owned by the developer to verify the subscription status. Only the user's Google email address (obtained with their OAuth consent) is sent, solely to confirm whether an active PRO license exists. **No other personal data is stored or processed in this flow.**

### 4. Permission Justifications
Watchlist+ only requests permissions strictly required to provide its core features:

| Permission | Purpose & Justification |
| :--- | :--- |
| `storage` / `unlimitedStorage` | Stores your watchlist, episode counters, profiles, and settings locally in the browser without running into quota limitations for large watchlists. |
| `tabs` / `activeTab` | Detects the series title and episode number in the current active tab on supported streaming platforms to update your watch progress automatically. It never reads data outside supported video pages. |
| `notifications` | Sends local browser notifications for upcoming calendar releases or when an automatic backup completes. |
| `alarms` | Schedules background routines for automated backup intervals and upcoming release checks. |
| `downloads` | Saves your exported backup `.json` files directly to your local "Downloads" directory. |
| `identity` | Used exclusively to authenticate the user with their Google account via OAuth 2.0, in order to sync backups to Google Drive and verify PRO plan status. No other services or account data are accessed. |
| `host_permissions` (streaming sites) | A detection script is injected into streaming site pages to automatically identify the series the user is watching. Only the URL and page title are read; this data is never transmitted to any external server. |

### 5. Third-Party Services and Analytics
Watchlist+ **DOES NOT** use:
- Telemetry, tracking, or analytics libraries (e.g. Google Analytics).
- Advertising networks.
- Tracking cookies.
- Behavioral monitoring services.

### 6. Data Ownership and Export
You have full ownership of your data. You can export and import your entire library at any time in standard JSON format. Optionally, you may enable automatic sync to your own Google Drive account.

### 7. Contact
For any questions regarding this Privacy Policy, please open an issue in the official project repository.

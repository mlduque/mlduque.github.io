# Email Seguro

> **Versión beta.** Proyecto en desarrollo: estamos añadiendo nuevas herramientas y algunas funciones pueden cambiar.

Herramientas gratuitas para proteger tu dominio, reconocer emails de estafa, probar tus campañas antes de enviarlas y mantener sana tu base de datos. Creadas por una profesional de la entregabilidad del email.

👉 **Pruébalas aquí:** [mlduque.github.io](https://mlduque.github.io/)

La web tiene once herramientas y una sección de guías, cada una en su pestaña:

- **Auditoría completa:** [mlduque.github.io/#auditoria](https://mlduque.github.io/#auditoria)
- **Mi dominio:** [mlduque.github.io/#dominio](https://mlduque.github.io/#dominio)
- **Analizar un email:** [mlduque.github.io/#email](https://mlduque.github.io/#email)
- **Probar mi campaña:** [mlduque.github.io/#campana](https://mlduque.github.io/#campana)
- **Mi base de datos:** [mlduque.github.io/#bbdd](https://mlduque.github.io/#bbdd)
- **Analizador de informes DMARC:** [mlduque.github.io/#dmarc](https://mlduque.github.io/#dmarc)
- **Calculadora de warm-up:** [mlduque.github.io/#warmup](https://mlduque.github.io/#warmup)
- **Test de bandeja:** [mlduque.github.io/#bandeja](https://mlduque.github.io/#bandeja)
- **¿Qué plataforma lo envió?:** [mlduque.github.io/#plataforma](https://mlduque.github.io/#plataforma)
- **Traductor de rebotes:** [mlduque.github.io/#rebotes](https://mlduque.github.io/#rebotes)
- **Generador de SPF, DMARC y BIMI:** [mlduque.github.io/#generador](https://mlduque.github.io/#generador)
- **Guías y glosario:** [mlduque.github.io/#guias](https://mlduque.github.io/#guias)

---

## Auditoría completa de un email (nuevo)

Envíate una prueba de tu campaña, sube el email (.eml) y la web ejecuta más de 40 comprobaciones a la vez, con un único informe de **apto, mejorable o no apto**, descargable en **PDF**:

- **Autenticación del envío:** SPF, DKIM, DMARC y alineación del Return-Path y de la firma DKIM.
- **Infraestructura y reputación:** IP de envío, DNS inverso (PTR y FCrDNS), cifrado TLS, listas negras de IP y dominio, y Sender Score.
- **Registros DNS del dominio,** validados según los estándares RFC, incluida la clave DKIM usada en el envío.
- **Cabeceras al estilo Rspamd:** Message-ID, fecha, MIME, destinatario, asunto codificado, versión de texto, Reply-To y más.
- **Contenido:** puntuación tipo SpamAssassin y peso del email.
- **Cumplimiento legal y marketing:** baja en un clic, pie legal, CTA y enganche.
- **Requisitos de Gmail y Yahoo** para envíos masivos.
- **Plataforma de envío** detectada.

Incluye un **historial** de auditorías y dominios comprobados que se guarda solo en tu navegador (sin el contenido de los emails).

---

## 1. ¿Está protegido tu dominio?

Desde 2024, Gmail y Yahoo exigen que los dominios que envían emails estén autenticados, y Microsoft se sumó en 2025. Si tu dominio no lo está, tus correos pueden acabar en spam o ser rechazados, y cualquiera podría enviar emails falsos en tu nombre.

Esta herramienta está pensada para pymes, autónomos y freelancers que no tienen un equipo técnico detrás: te dice qué está bien, qué falta y exactamente qué registro añadir.

### Cómo se usa

1. Escribe tu dominio (por ejemplo, *tuempresa.com*). También puedes pegar tu email o la dirección de tu web.
2. Pulsa **Comprobar dominio**.
3. Verás un resultado general (**Protegido**, **Mejorable** o **Expuesto**), si cumples los requisitos de Gmail, Yahoo y Microsoft, y un semáforo para cada comprobación.
4. Donde haya algo en amarillo o rojo, encontrarás los pasos para arreglarlo y el registro DNS listo para copiar.

### Qué revisa

**Autenticación del email**
- **MX (recepción de correo):** si tu dominio puede recibir emails y con qué proveedor.
- **SPF (remitentes autorizados):** si existe, si es único, si termina correctamente y si supera el límite de 10 consultas DNS.
- **DKIM (firma digital):** busca la firma con los selectores más habituales y, para cada clave, muestra su tamaño exacto en bits y si es segura según las buenas prácticas: insegura (menos de 1024), débil (1024), segura (2048) o muy segura (3072 o más). También reconoce claves Ed25519.
- **DMARC (política anti-suplantación):** si existe, qué nivel de protección aplica y si recibes informes.
- **BIMI (logo de marca):** si tu logo puede aparecer junto a tus emails. Es opcional.
- **Validación de sintaxis según los RFC:** detecta errores en SPF (RFC 7208), DMARC (RFC 7489) y claves DKIM, y comprueba la autorización de los informes DMARC enviados a dominios externos.
- **Seguridad avanzada:** DNSSEC, MTA-STS y TLS-RPT.

**Reputación y web**
- **Reputación del remitente:** consulta la reputación de las IPs de envío (las que encuentra y la que tú indiques) en Sender Score, HostKarma y DNSWL, y su DNS inverso (PTR y FCrDNS), con enlaces a Sender Score, Cisco Talos, Google Postmaster Tools y Microsoft SNDS.
- **Listas negras:** revisa tu dominio en 5 listas de dominios (Spamhaus DBL, SURBL, URIBL…) y las IPs asociadas en 9 listas de IPs (Spamhaus ZEN, SpamCop, Barracuda…). Si apareces en alguna, te explica cómo salir.
- **Certificado SSL:** indica si el dominio tiene web asociada y si esa web tiene certificado SSL. Si lo tiene, muestra quién lo emitió, sus fechas de validez, cuántos días le quedan, qué dominios cubre (incluido www) y qué autoridades pueden emitir certificados para tu dominio (registro CAA).

El informe del dominio también se puede **descargar en PDF**.

---

## 2. ¿Este email es de fiar?

Pega un email sospechoso y en segundos te dice si tiene pinta de estafa, y por qué.

### Cómo se usa

1. Copia el email sospechoso (si puedes, incluye la línea del remitente).
2. Pégalo y pulsa **Analizar email**.
3. Recibirás un veredicto (**Peligroso**, **Sospechoso** o **Sin alertas**), un nivel de riesgo de 0 a 100 y la explicación de cada señal.

Para un análisis más preciso, usa la pestaña **Cabeceras**. En la propia web tienes una guía para copiarlas desde Gmail, Outlook, Apple Mail y Yahoo.

### Qué revisa

- **El remitente:** si el nombre dice ser una empresa conocida pero la dirección no es suya, si escribe desde una cuenta gratuita haciéndose pasar por una empresa y si las respuestas irían a otra dirección.
- **Los enlaces:** webs que imitan marcas (incluso cambiando letras por números), enlaces acortados, direcciones IP, terminaciones de riesgo y enlaces cuyo texto no coincide con el destino.
- **El mensaje:** prisa o amenazas, peticiones de contraseñas o datos de tarjeta, premios o reembolsos, el timo del paquete retenido, saludos genéricos y adjuntos peligrosos.
- **La autenticación (modo cabeceras):** SPF, DKIM y DMARC, y la **alineación** del Return-Path (SPF) y de la firma DKIM con el dominio del remitente.

---

## 3. ¿Tu campaña llegará a la bandeja?

Para marketers y cualquiera que envíe newsletters. Escribe el remitente, el asunto y el preheader, y pega el HTML de tu email.

### Qué hace

- **Vista previa en la bandeja:** muestra cómo se verá tu email en un móvil, en Gmail escritorio y en Outlook escritorio, e indica si el asunto o el preheader se cortan. Si no has escrito preheader, muestra lo que verán tus lectores (el inicio del HTML).
- **Revisión del asunto y el preheader:** longitud, mayúsculas, exclamaciones, emojis, palabras típicas de spam, falsos RE: o FW: y palabras disfrazadas.
- **Revisión del HTML:** peso (Gmail recorta a partir de 102 KB), proporción de texto e imágenes, imágenes sin texto alternativo, enlace de baja, texto oculto o invisible, enlaces acortados, a IPs o engañosos, scripts y formularios, y frases de spam.
- **Análisis de email marketing:** puntúa la llamada a la acción (CTA), la capacidad de enganche y el cumplimiento legal europeo del pie (baja, remitente, privacidad, motivo de recepción).
- **Email completo (.eml):** si subes el email completo, revisa además la baja en un clic (List-Unsubscribe y List-Unsubscribe-Post) y la alineación SPF/DKIM del envío real.
- **Test tipo SpamAssassin:** suma puntos con reglas equivalentes a las de SpamAssassin y los compara con el umbral habitual de 5.
- **Puntuación de 0 a 100 con semáforo.**
- **Arreglos de un clic:** asunto sugerido, preheader sugerido, añadir texto alternativo, añadir enlace de baja, añadir un botón CTA, añadir un pie legal completo y acceso directo para excluir inactivos de tu lista.
- **Vista previa del HTML** en tamaño móvil y escritorio.

---

## 4. ¿Está sana tu base de datos?

Sube tu lista de contactos en CSV o Excel, pégala desde una hoja de cálculo o comprueba un solo contacto.

### Qué hace

- Detecta **emails inválidos, duplicados, errores de escritura** (gmial.com, hotmial.com…), **desechables**, **genéricos** (info@, ventas@…), **de prueba** y **dominios que no reciben correo**.
- Si el archivo tiene fechas de última apertura o clic, clasifica a los contactos en **activos** (90 días o menos), **en riesgo** (91 a 180 días), **inactivos** (más de 180 días) y **sin actividad**.
- Si tiene una columna de estado, detecta **bajas, rebotes y quejas**.
- Da una **puntuación de salud de 0 a 100 con semáforo** y muestra los dominios más frecuentes.
- **Limpieza de un clic:** eliges qué excluir y descargas la lista limpia (con los errores de escritura corregidos), los contactos excluidos con el motivo, o los inactivos para una campaña de reactivación.

---

## Analizador de informes DMARC (nuevo)

Sube los informes DMARC agregados que te envían Google, Microsoft o Yahoo (.xml, .zip o .gz, tal como llegan, uno o varios a la vez) y verás:

- el **porcentaje de emails que pasan DMARC**, DKIM y SPF alineados;
- cada **fuente de envío** con su IP, su nombre de servidor y la **plataforma detectada** (SendGrid, Mailchimp, Google…);
- qué fuentes **pasan**, cuáles son **legítimas pero fallan** y cuáles son **posibles suplantaciones**;
- **qué hacer**: configurar DKIM en las herramientas que fallan y cuándo subir la política a quarantine o reject.

Los informes se descomprimen y analizan en el navegador: no salen de tu ordenador. El informe se puede descargar en PDF y la IA puede explicarlo.

---

## 5. Calculadora de warm-up

Indica si el dominio o la IP son nuevos o tienen historial, el volumen diario al que quieres llegar y, si quieres, una fecha objetivo. Obtendrás un plan día a día con los emails por día y por hora, avisos si el plazo es demasiado corto y el plan descargable en CSV.

---

## 6. Test de bandeja

Explica cómo funciona un test de bandeja (inbox placement) y recomienda herramientas gratuitas para hacerlo: Warmy, Mail-tester, GlockApps, MXToolbox, Google Postmaster Tools y Microsoft SNDS. También explica cómo montar tu propia lista de semillas.

---

## 7. ¿Qué plataforma lo envió?

Pega el email original (o sus cabeceras) o sube el archivo .eml y la web identifica con qué plataforma se envió, entre **86 plataformas**: Mailchimp, Klaviyo, SendGrid, Amazon SES, Brevo, HubSpot, Salesforce Marketing Cloud, ActiveCampaign, Acumbamail, Mailrelay, emBlue, MDirector, Doppler, MailerLite, Substack y muchas más. Muestra las pruebas (Return-Path, firmas DKIM, servidores, cabeceras propias y enlaces de seguimiento), el nivel de confianza y si el remitente usa dominios propios (marca blanca).

---

## Traductor de rebotes (nuevo)

Pega el mensaje de error que te devuelve un servidor (por ejemplo, «550 5.7.1 …» o el aviso completo de «Mail Delivery Subsystem») y la web te dice:

- **qué tipo de rebote es:** duro, blando, bloqueo, autenticación, configuración o respuesta automática;
- **qué significa, por qué ha pasado y qué hacer**, paso a paso;
- **si debes borrar el contacto** de tu lista o no;
- **el código pieza a pieza** (clase, tema y detalle según el estándar), con los códigos propios de Gmail, Microsoft, Yahoo y Apple.

Incluye una base de **326 respuestas reales de 33 proveedores y filtros antispam** (Gmail, Outlook, Microsoft 365, Yahoo, Apple iCloud, GMX/WEB.DE/IONOS, Orange, La Poste, Free, Comcast, AT&T, Yandex, Mail.ru, QQ, Zoho, GoDaddy, Rackspace, Titan, Proton, Mimecast, Proofpoint, Barracuda, Cisco, Trend Micro y más). Si el mensaje coincide con una de ellas, la web te muestra la respuesta documentada, el proveedor y el enlace a su documentación oficial. Clasifica cada caso en más de 45 situaciones distintas, con explicaciones en los cinco idiomas. Incluye explicación con IA.

Las respuestas reales proceden de [SMTP Field Manual](https://smtpfieldmanual.com/) (Postmark/ActiveCampaign) y [smtp.codes](https://smtp.codes/) (Neatnik y Faisal Misle), ambos con licencia MIT. Las explicaciones y traducciones son propias.

## Generador de SPF, DMARC y BIMI (nuevo)

Asistentes paso a paso para crear registros correctos, listos para copiar en tu proveedor de DNS:

- **SPF:** marca tus herramientas (Google Workspace, Microsoft 365, SendGrid, Brevo, Amazon SES…), añade IPs o «include» propios y elige la política. Cuenta las búsquedas DNS y, con «Comprobar en DNS», calcula el total real (máximo 10) y te enseña el SPF que ya tienes publicado.
- **DMARC:** elige la política (observar, spam o rechazar), las direcciones de informes y las opciones avanzadas. Te avisa si los informes van a otro dominio y te da el registro de autorización necesario.
- **BIMI:** genera el registro, comprueba si tu DMARC cumple el requisito y valida en tu navegador que el logo cumple el formato SVG Tiny PS.

## Guías y glosario (nuevo)

Seis guías prácticas (SPF, DKIM y DMARC; requisitos de Gmail, Yahoo y Microsoft; por qué los emails van a spam; listas negras; rebotes; BIMI) y un glosario con buscador de 40 términos de entregabilidad, en los cinco idiomas. Cada guía tiene su propio enlace, por ejemplo [mlduque.github.io/#guias/autenticacion](https://mlduque.github.io/#guias/autenticacion).

## Idiomas

La web está disponible en **español, inglés, italiano, francés y portugués**, incluidos todos los resultados de los análisis y los informes en PDF. Detecta el idioma de tu navegador y puedes cambiarlo en el selector de la barra superior. El asistente de IA responde en el idioma elegido.

---

## Asistente con inteligencia artificial

Cada herramienta incluye el botón **«Explícamelo y dime cómo arreglarlo»**. La IA revisa los resultados del análisis y te explica, en lenguaje sencillo:

- **qué está mal** y **por qué** importa,
- **qué tienes que cambiar exactamente**, con los textos, registros DNS o fragmentos de HTML corregidos listos para copiar,
- y por dónde empezar.

En el probador de campañas, además, propone asuntos y preheaders alternativos; en la base de datos, un plan de limpieza y una campaña de reactivación.

La IA funciona a través de un pequeño intermediario seguro (un Cloudflare Worker) que guarda la clave de la API, de modo que nunca queda expuesta en la web. Por defecto usa **Gemini de Google**, que tiene un plan gratuito.

---

## Tu privacidad

Esta web no usa cookies, ni analítica, ni publicidad, y las tipografías se sirven desde la propia web (sin conexión a Google Fonts). Tienes todos los detalles en la [política de privacidad](https://mlduque.github.io/#privacidad) y el [aviso legal](https://mlduque.github.io/#aviso-legal).


- **Analizar un email:** el email no sale de tu dispositivo. Todo se analiza en tu navegador.
- **Comprobar un dominio:** solo se consulta información pública: el DNS (Google Public DNS, con Cloudflare como respaldo), los registros públicos de certificados (Cert Spotter y crt.sh) y las listas negras.
- **Probar una campaña:** el asunto, el preheader y el HTML se analizan en tu navegador.
- **Analizar una base de datos:** la lista no sale de tu dispositivo. Solo se consulta en el DNS público si los dominios de empresa reciben correo, nunca las direcciones.

- **Explicación con IA (opcional):** solo se envía algo cuando marcas la casilla de consentimiento y pulsas el botón. Antes de enviarlo se oculta la parte personal de las direcciones de email. En el detector de phishing y en el probador de campañas se envía el contenido analizado; en la base de datos, solo estadísticas, nunca los contactos. En el plan gratuito de Gemini, Google puede usar el contenido para mejorar sus productos.

No se guarda nada.

## Ten en cuenta

Son herramientas orientativas: ningún análisis automático es infalible. El test tipo SpamAssassin es una estimación del contenido: el filtro real también tiene en cuenta la reputación, el dominio y las cabeceras. Algunas listas negras, como Spamhaus, no responden a consultas desde servicios DNS públicos; en ese caso aparecen como «No disponible» y puedes comprobarlas en su web oficial. Antes de cambiar registros DNS, confirma los valores con tu proveedor de correo.

## Sobre la autora

Más información en la página [Sobre mí](https://mlduque.github.io/#sobre-mi). ¿Sugerencias, errores o propuestas? Escríbeme desde la página de [contacto](https://mlduque.github.io/#contacto).


Creado por **María Luisa Duque**, Email Deliverability Manager.

Trabajo cada día para que los emails legítimos lleguen a la bandeja de entrada. Con estas herramientas quiero que cualquier persona pueda reconocer los que no lo son, y que cualquier negocio, por pequeño que sea, pueda proteger su dominio, cuidar su lista y enviar mejores campañas sin necesidad de ser experto.

[Conecta conmigo en LinkedIn](https://www.linkedin.com/in/marialuisaduque/)

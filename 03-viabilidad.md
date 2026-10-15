# 3. Estudio de viabilidad

<!-- FASE 1 · Se cierra en la S3 (13 de octubre). -->

## 3.1. Viabilidad técnica

<!--
¿Se puede hacer con los recursos reales del aula? RAM del PC anfitrión,
número de máquinas virtuales, acceso SSH entre equipos, horas disponibles.
Si veis algún riesgo, decid cómo pensáis mitigarlo.
-->
* **Recursos en el aula:** El desarrollo se realiza en un ordenador anfitrión utilizando máquinas virtuales mediante VirtualBox[cite: 4]. Con una configuración estándar de aula, es posible desplegar de forma simultánea de 3 a 4 máquinas virtuales ligeras (como el punto de control/cortafuegos, servidor de base de datos y servidor web con WordPress/WooCommerce) sin afectar negativamente al rendimiento general del sistema.
* **Conectividad y horas:** El acceso remoto entre equipos mediante SSH y la dedicación temporal estimada de 3 horas semanales (unas 47 horas totales hasta febrero) se ajustan perfectamente a los plazos establecidos[cite: 4, 5].
* **Mitigación de riesgos:** Para prevenir la saturación de memoria RAM en el equipo anfitrión, se emplearán sistemas operativos base sin entorno gráfico (servidores) en las máquinas virtuales y se distribuirán los servicios de manera eficiente según la arquitectura de red planteada.

## 3.2. Viabilidad económica

<!--
Coste estimado si la infraestructura se desplegara de verdad. Indicad la
fuente de cada precio. El software libre cuesta 0 € en licencias, pero no
en horas de trabajo: valorad también eso.
-->

Para calcular el coste real de desplegar esta infraestructura en servidores de producción reales con dominio público y compararlo con el límite de 6.000 € y 100 € mensuales fijado por la dirección[cite: 5], se presenta el siguiente desglose:

| Concepto | Coste estimado | Fuente |
|----------|----------------|--------|
| Hosting / servidores (VPS optimizado para WooCommerce) | 12,58 € / mes (IVA incl.) | OVHcloud (Plan VPS-3 o similar) |
| Dominio (ej. .es o .com) | 12,00 € / año | Dinahosting / OVH |
| Certificado TLS | 0 € (Let's Encrypt) | Autoridad de certificación libre |
| Licencias (Software libre: WordPress, Linux, etc.) | 0 €[cite: 4] | Política de la empresa (Open Source)[cite: 4] |
| Horas de trabajo (130 horas a 30 €/h) | 3.900,00 € | Tarifa estándar de mercado para perfil técnico junior/intermediario |
| **Total inicial / recurrente** | **Inversión inicial:** 3.912,00 € <br>**Coste mensual:** ~13 € / mes | *Inferior al presupuesto máximo del cliente (6.000 € y 100 €/mes)[cite: 5]* |

*Nota económica:* El coste global del proyecto se encuentra muy por debajo del límite de 6.000 € estipulados por la dirección[cite: 5], y el gasto recurrente mensual (~13 €) respeta holgadamente el tope máximo de 100 € mensuales permitidos para el mantenimiento[cite: 5].

## 3.3. Viabilidad legal

<!--
Obligaciones de una tienda online que recoge datos de clientes (RGPD,
LSSI-CE). Lo importante aquí es qué implican para el diseño: qué datos se
piden y cuáles no, dónde se guardan, quién accede a ellos. El detalle técnico
de las medidas se desarrolla en el apartado 6.3.
-->

Al recopilar información de carácter personal de los usuarios (nombre, dirección de envío, teléfono, correo electrónico e historial de compras)[cite: 3], la tienda online debe ajustarse de manera rigurosa al **RGPD** (Reglamento General de Protección de Datos) y a la **LSSI-CE** (Ley de Servicios de la Sociedad de la Información y de Comercio Electrónico)[cite: 4].

* **Impacto en el diseño:**
  * Se solicitarán únicamente los datos imprescindibles para gestionar el envío y la facturación, aplicando el principio de minimización de datos.
  * El proceso de compra permitirá realizar pedidos sin necesidad de registro obligatorio previo[cite: 2], garantizando la transparencia y la obtención del consentimiento explícito mediante casillas de aceptación no marcadas por defecto.
  * Los datos se custodiarán en bases de datos protegidas y cifradas bajo el control exclusivo de la empresa, aislando la capa web de la capa de almacenamiento de datos conforme a las directrices de seguridad.
  * El acceso a la información estará estrictamente segmentado por roles de usuario (dirección, personal de tienda y clientes)[cite: 2].

## 3.4. Sostenibilidad y economía circular

<!--
Módulo SASP. Dos partes:
1. Criterios de sostenibilidad en el propio proyecto (virtualización frente a
   hardware físico, software libre, PKI propia frente a dependencias externas...).
2. El catálogo y el modelo de negocio de la tienda desde la economía circular
   (reparación, segunda mano, envases, logística...).
-->

* **Criterios de sostenibilidad en el proyecto:**
  * Se fomenta el uso exclusivo de **software libre**, eliminando costes de licencias y dependencias tecnológicas cerradas[cite: 4].
  * La adopción de la **virtualización** durante el desarrollo optimiza el uso de recursos y evita la necesidad de hardware físico adicional en las pruebas del aula[cite: 4].
  * La arquitectura de red y los mecanismos de seguridad se diseñan con criterios de eficiencia para evitar procesamientos innecesarios y reducir el consumo energético.
* **Modelo de negocio y economía circular aplicado a Bintransfer:**
  * La actividad principal de digitalización de figuras 3D apoya la economía circular al facilitar la **reparación digital de piezas descatalogadas**, la producción bajo demanda para evitar stocks innecesarios de elementos físicos y la optimización de la logística de proximidad para reducir la huella de carbono asociada al envío de los modelos procesados.
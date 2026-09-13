INTEGRANTES:

Shelcy Rondon Muñoz

Samuel Moreno Mesa

Contexto de la organización

**Empresa:** Ecopetrol S.A. (Empresa del sector energético y de hidrocarburos en Colombia).  
**Actividad y Sistemas:** Deduce, refina y transporta hidrocarburos a nivel nacional e internacional. Maneja sistemas de tecnología de la información (TI) como **SAP ERP** para la gestión financiera, comercial y de cadena de suministro; y sistemas de tecnología operativa (OT/SCADA) para la automatización, monitoreo y control en tiempo real de refinerías y oleoductos.  
**Riesgos y preocupaciones principales:** Interrupción de operaciones por ciberataques a la red industrial (OT/SCADA), riesgo financiero e infracciones regulatorias frente a entes de control (Superfinanciera, SEC de EE. UU. por cotizar en bolsa), y fuga de información geológica o comercial estratégica.

Elección de marcos y orden de aplicación

1. **COBIT (Nivel de Gobierno Corporativo y Cumplimiento):**Marco sombrilla.

2. **NIST CSF / ISO 27001 (Nivel de Ciberseguridad e Infraestructura Crítica / OT):** Marco de protección de activos.

3. **ITIL (Nivel de Operación de Servicios e Infraestructura TI):**Marco de gestión de servicios.

Justificación técnica del orden y combinación

 **1º Aplicar COBIT:** Al ser una empresa de economía mixta que cotiza en la Bolsa de Valores de Colombia y en la de Nueva York (NYSE), Ecopetrol debe cumplir con estrictas regulaciones corporativas y financieras (como la Ley Sarbanes-Oxley / SOX). COBIT es indispensable en primer lugar para auditar que el gobierno de TI asegure el cumplimiento normativo, la gestión integral de riesgos corporativos y la alineación estratégica entre la tecnología y el negocio.

 **2º Aplicar NIST CSF / ISO 27001:** Ecopetrol forma parte de la infraestructura crítica nacional. Un ataque cibernético a un oleoducto o refinería (entorno OT) paralizaría al país. Se aplica NIST CSF (o ISO 27001/27019) inmediatamente después de COBIT para evaluar la resiliencia en ciberseguridad, asegurando la detección, protección y respuesta ante amenazas que puedan comprometer tanto la red administrativa como la operación industrial.

 **3º Aplicar ITIL:** La continuidad operativa del corporativo y la disponibilidad de sistemas como SAP para la liquidación de regalías, nómina, compras y facturación de derivados requieren procesos estandarizados. ITIL permite auditar la gestión de eventos, incidentes corporativos y cambios en la infraestructura para evitar caídas del servicio informático que congelen la operación comercial.

Evidencias solicitadas por marco

1\. COBIT

 **Reportes de cumplimiento SOX (Sección 404\) y matriz de Controles Generales de TI (ITGC):** Para verificar los controles sobre acceso a datos financieros, segregación de funciones y gestión de cambios dentro de SAP.

 **Matriz de Alineación Estratégica y Gobierno de TI:** Actas de reuniones del Comité Directivo de Tecnología donde se evidencie la aprobación del plan estratégico de TI (PETI) y la asignación presupuestal ponderada según riesgos corporativos.

2\. NIST CSF / ISO 27001

 **Diagramas de arquitectura de segmentación de red (Modelo Purdue):** Documentación técnica que demuestre el aislamiento e interconexión segura (firewalls, DMZ) entre la red de TI corporativa y la red de OT/SCADA en refinerías.

 **Plan de Respuesta a Incidentes de Ciberseguridad y registros de simulacros:** Protocolos probados para contener amenazas cibernéticas en infraestructura crítica, junto con las evidencias de las últimas pruebas de contingencia realizadas en el año.

3\. ITIL

 **Bitácora y reportes del Centro de Operaciones de Red / Servicio (NOC/Service Desk):** Trazabilidad de tickets de incidentes de TI, con medición de tiempos de solución y cumplimiento de Acuerdos de Nivel de Servicio (SLA) para aplicaciones críticas.

 **Plan de Continuidad del Negocio (BCP) y Plan de Recuperación ante Desastres (DRP) de TI:** Procedimientos documentados y actas de pruebas de restauración de copias de seguridad de las bases de datos de SAP ante una eventualidad grave.  
 


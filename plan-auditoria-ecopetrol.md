**Plan de auditoría: acceso remoto de terceros a la red OT/SCADA**

**Integrantes:**

* Shelcy Rondon

* Samuel Moreno Mesa

**Caso:** Ecopetrol S.A.

**Riesgo auditado:** R-01 (matriz de riesgos vigente)

# **Identificación del equipo y del caso**

Este documento continúa el trabajo realizado sobre Ecopetrol S.A., empresa del sector energético e hidrocarburos que opera refinerías y oleoductos en Colombia. Se mantiene el mismo caso, los mismos marcos de referencia (COBIT, NIST CSF/ISO 27001 e ITIL) y la matriz de riesgos construida en el taller anterior. No se realizó ningún cambio de caso ni de equipo de trabajo.

# **1\. Contexto y riesgo seleccionado**

El taller anterior identificó cinco riesgos sobre procesos y activos de Ecopetrol relacionados con TI, OT y cumplimiento. De esa matriz se selecciona el riesgo **R-01**, por ser el de mayor nivel (20, de un máximo de 25\) y por involucrar infraestructura crítica nacional.

**Referencia en la matriz de riesgos:**

| Campo | Contenido (de la matriz vigente) |
| :---- | :---- |
| ID | R-01 |
| Activo o proceso afectado | Red de automatización y control industrial (OT/SCADA) de refinerías y oleoductos |
| Amenaza | Atacante externo (p. ej. grupo de ransomware industrial) que explota la conexión remota de un contratista de mantenimiento |
| Vulnerabilidad | La VPN de contratistas no cuenta con autenticación multifactor ni segmentación de red hacia la zona OT |
| Riesgo | Un atacante podría obtener acceso a la red de control industrial a través de la conexión remota de un contratista y detener la operación de una refinería |
| Probabilidad | 4 — el acceso remoto de terceros es un vector frecuente en incidentes del sector industrial y no hay evidencia de controles compensatorios |
| Impacto | 5 — una intrusión en la red OT puede detener físicamente la operación de una refinería u oleoducto |
| Nivel de riesgo | 20 (4 × 5\) |
| Control actual o evidencia | No se encontró evidencia documentada de MFA ni de segmentación tipo Purdue para accesos remotos de terceros |
| **Control propuesto (taller anterior)** | Implementar MFA obligatorio y segmentación de red (DMZ) para todas las conexiones remotas de contratistas a la red OT, con revisión trimestral de accesos activos |

**Por qué vale la pena auditar este riesgo (no solo por el puntaje):**

El proceso de administración de accesos remotos de terceros es la puerta de entrada más directa desde una red externa hacia la infraestructura de control industrial. A diferencia de un riesgo puramente financiero o de información, este compromete la continuidad física de la operación —una interrupción prolongada afecta el suministro nacional de combustibles— y constituye infraestructura crítica bajo el marco regulatorio colombiano. Además, es un riesgo con control propuesto pero sin evidencia de implementación verificada, lo que lo hace idóneo para una auditoría de diseño y operación, en lugar de un riesgo puramente especulativo.

# **2\. Justificación y objetivo de auditoría**

**Objetivo principal de auditoría:**

*Determinar si las conexiones remotas de contratistas de mantenimiento hacia la red de control industrial (OT/SCADA) cuentan con autenticación multifactor y segmentación de red conforme al procedimiento vigente, durante el periodo definido.*

Este objetivo plantea una condición verificable (existencia y aplicación de MFA y segmentación) en lugar de una actividad genérica como “auditar la seguridad de la red OT”.

# **3\. Alcance funcional**

| Elemento | Definición |
| :---- | :---- |
| Proceso o función | Gestión de accesos remotos de contratistas de mantenimiento a la red de control industrial (autorización, autenticación y segmentación de la conexión) |
| Sistema o componente | Infraestructura de VPN/acceso remoto utilizada por contratistas externos, y los puntos de segmentación de red (firewalls, DMZ) entre la red corporativa de TI y la red OT, en al menos una refinería representativa |
| Población | Conexiones remotas de contratistas registradas durante el periodo de revisión; cuentas de contratista con permiso de acceso remoto activo |
| Periodo | Últimos 6 meses anteriores a la fecha de inicio de la auditoría — periodo razonable para observar tanto el comportamiento recurrente de accesos como la vigencia de las cuentas asociadas a contratos |
| Áreas o responsables | Área de Ciberseguridad/TI industrial (custodia de configuración de VPN y segmentación); área de Contratación/Supervisión de contratos de mantenimiento (origen y vigencia de los contratos de terceros) |
| Inclusiones | Conexiones remotas de contratistas hacia la red OT; configuración de autenticación y segmentación asociada a esas conexiones |
| Exclusiones | Accesos remotos de empleados internos de Ecopetrol (quedan fuera de este objetivo); conexiones físicas en sitio; otros riesgos de la matriz (R-02 a R-05) |

**Nota sobre la exclusión:** al excluir los accesos de empleados internos, la conclusión de esta auditoría se limita exclusivamente a la gestión de terceros y no permite afirmar nada sobre la seguridad general de los accesos a la red OT.

# **4\. Criterios de evaluación**

| Control a evaluar | Criterio (condición esperada) | Fuente | Estado |
| :---- | :---- | :---- | :---- |
| Autenticación multifactor en accesos remotos de terceros | Toda conexión remota de un contratista a la red OT debe autenticarse mediante un segundo factor, conforme a la política de acceso remoto vigente | Política interna de acceso remoto de Ecopetrol | Por confirmar mediante solicitud de la política vigente — no se tuvo acceso directo al documento |
| Segmentación de red entre TI corporativa y red OT | La conexión remota de un tercero debe ingresar a una zona desmilitarizada (DMZ) y no tener ruta directa a los sistemas de control (modelo de referencia Purdue) | Arquitectura de referencia Purdue / lineamientos NIST CSF (función “Protect”) | Criterio basado en una práctica de referencia del sector; se aplicaría si la organización la adoptó formalmente o se confirmaría como brecha si no existe documento equivalente |
| Vigencia del acceso frente al contrato | El acceso remoto de un contratista debe estar activo únicamente durante la vigencia de su contrato | Procedimiento de gestión de accesos de terceros | Por confirmar mediante solicitud del procedimiento vigente |

No se atribuye a COBIT, NIST CSF o ISO/IEC 27001 un porcentaje, plazo o control específico que no haya sido verificado; donde no se conoce la política interna, se deja explícito como pendiente de confirmar.

# **5\. Programa de trabajo**

| ID del riesgo | Control a evaluar | Criterio y fuente | Procedimiento | Población o muestra | Evidencia esperada |
| :---- | :---- | :---- | :---- | :---- | :---- |
| R-01 | Autenticación multifactor (MFA) en accesos remotos de terceros | Toda conexión remota de contratista a la red OT requiere segundo factor — política de acceso remoto (por confirmar) | Diseño: solicitar la política de acceso remoto vigente y la configuración del sistema de VPN/MFA; entrevistar al responsable de ciberseguridad industrial para entender cómo se exige el MFA al contratista. Operación: tomar una muestra de conexiones remotas registradas en el periodo y verificar en el log de autenticación si cada una exigió el segundo factor. | Registro de conexiones remotas de contratistas del periodo (6 meses); muestra propuesta de 25 conexiones o el 100 % si la población es menor a 25 | Política de acceso remoto; capturas o reportes de configuración del sistema de MFA; extracto del log de autenticación con marca de MFA exitoso/fallido por conexión muestreada |
| R-01 | Segmentación de red (DMZ) hacia la zona OT | Conexión remota no debe tener ruta directa a sistemas de control — referencia Purdue/NIST CSF (criterio de referencia) | Diseño: solicitar el diagrama de arquitectura de red vigente (segmentación TI/OT) y las reglas de firewall asociadas a la DMZ de accesos remotos. Operación: revisar una muestra de reglas de firewall activas y confirmar que el tráfico de la VPN de contratistas termina en la DMZ y no tiene regla directa hacia la red de control. | Reglas de firewall vigentes en los puntos de segmentación de al menos una refinería representativa | Diagrama de arquitectura de red; extracto de reglas de firewall activas; evidencia de la última revisión de esas reglas |
| R-01 | Vigencia del acceso frente al contrato | El acceso remoto debe estar activo solo durante la vigencia del contrato — procedimiento de gestión de accesos de terceros (por confirmar) | Diseño: solicitar el procedimiento de alta/baja de accesos de contratistas y entrevistar al área de Contratación sobre cómo se notifica la finalización de un contrato a TI. Operación: comparar el listado de cuentas de contratista con acceso remoto activo contra el listado de contratos de mantenimiento vigentes a la fecha de corte, e identificar cuentas activas sin contrato vigente. | Listado completo de cuentas de contratista con acceso remoto activo a la fecha de corte, contrastado contra el listado de contratos vigentes | Listado de cuentas activas; listado de contratos vigentes; relación de excepciones (cuentas activas sin contrato vigente), si existieran |

**Sobre la entrevista:** las entrevistas con el área de Ciberseguridad y de Contratación se usarían únicamente para entender el diseño del proceso; en ningún caso sustituirían la revisión de logs, reglas de firewall y listados de cuentas como evidencia de que el control efectivamente operó.

**Posibles excepciones a buscar:** conexiones remotas sin registro de MFA exitoso; reglas de firewall que permitan tráfico directo de la VPN de contratistas hacia la red de control; cuentas de contratista activas después de la fecha de finalización de su contrato.

# **6\. Responsables, cronograma, supuestos y limitaciones**

## **Cronograma propuesto**

| Fase | Actividad | Duración estimada | Responsable (equipo) |
| :---- | :---- | :---- | :---- |
| Preparación | Definir objetivo, alcance y criterios; preparar solicitudes de información | 3 días | Todo el equipo |
| Solicitud de información | Solicitar política de acceso remoto, diagrama de red, reglas de firewall, listados de cuentas y contratos | 5 días (depende de respuesta de la organización) | Integrante encargado de enlace con TI/Ciberseguridad |
| Revisión de diseño | Analizar política, diagrama y procedimiento frente al criterio definido | 3 días | Integrante encargado de criterios |
| Revisión de operación | Contrastar muestra de logs, reglas de firewall y listado de cuentas vs. contratos | 4 días | Integrante encargado de evidencia |
| Cierre | Consolidar hallazgos preliminares, redactar excepciones encontradas y limitaciones | 2 días | Todo el equipo |

## **Qué podría ejecutarse realmente vs. qué queda como planificación**

Dado que el equipo no tiene acceso real a los sistemas de Ecopetrol, **todo el programa de trabajo queda a nivel de planificación**: se diseñó qué se solicitaría, compararía y documentaría, pero no se ejecutó ninguna revisión real de logs, reglas de firewall o listados de cuentas. Ninguna sección de este documento presenta un hallazgo o una conclusión sobre si el control opera o no.

## **Supuestos, hechos y pendientes**

| Tipo | Elemento |
| :---- | :---- |
| Hecho comprobado | Ecopetrol opera refinerías y oleoductos con sistemas OT/SCADA, y cotiza en bolsa en Colombia y en NYSE (contexto del primer trabajo) |
| Supuesto | La VPN de contratistas no cuenta hoy con MFA ni segmentación estricta hacia la zona OT (supuesto ya declarado en la matriz de riesgos, no verificado directamente) |
| Supuesto | El acceso remoto de contratistas se gestiona mediante una política formal, aunque el equipo no tuvo acceso a su contenido |
| Información por solicitar | Política de acceso remoto vigente; diagrama de arquitectura de red y reglas de firewall; procedimiento de alta/baja de accesos de terceros; listado de cuentas activas y de contratos vigentes; logs de autenticación del periodo |
| Propuesta del equipo | El objetivo, el alcance, los tres criterios, los tres procedimientos, la muestra sugerida (25 conexiones) y el cronograma son diseño propio del equipo para este taller |

**Limitación principal:** al no tener acceso a la organización, no es posible confirmar si los criterios “por confirmar” corresponden a una política realmente vigente. Si la política no existe, el hallazgo del diseño sería en sí mismo una excepción (ausencia de criterio formal), lo cual debería declararse como tal en una ejecución real.

# **7\. Fuentes y referencia a la matriz completa**

* Matriz de riesgos vigente de Ecopetrol S.A. (taller anterior), fila R-01, anexa a este documento en el mismo repositorio.

* Primer trabajo: elección de marcos de referencia (COBIT, NIST CSF/ISO 27001, ITIL) y evidencia propuesta por marco.

* Modelo de referencia Purdue para segmentación de redes TI/OT (referencia de segundo nivel usada como criterio de arquitectura).

* NIST Cybersecurity Framework, función “Protect” (PR.AC — control de acceso), como referencia conceptual para el criterio de MFA y segmentació


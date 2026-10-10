**Matriz inicial de riesgo**

## Integrantes

* Shelcy Rondón 

* Samuel Moreno Mesa

## Caso y contexto actualizado

Ecopetrol S.A. gestiona la red de automatización industrial (OT/SCADA) para sus refinerías y para sus oleoductos, así como la aplicación del módulo financiero de SAP ERP para pagos, nómina y liquidación de regalías. Este taller aborda el proceso para gestionar cuentas y accesos (empleados, ingenieros de planta y contratistas de mantenimiento) a la red OT/SCADA y a los módulos críticos de SAP, ya que es la preocupación de ciberseguridad y continuidad operativa que se identificó en la anterior sesión del taller. Los marcos de referencia (COBIT, NIST CSF/ISO 27001 e ITIL), se mantienen en el mismo orden de aplicación definido anteriormente.

## Supuestos

* La información real, de la propia compañía Ecopetrol, no fue suficientemente accesible, dado que la matriz se fundamenta en premisas razonables tomadas de las prácticas del sector energético y el sector industrial; aquí esas premisas no se presentan como hechos probados:

* Se supone que los contratistas de mantenimiento tienen acceso remoto a la red OT sin autenticación multifactor y/o segmentación estricta, como es común en los entornos de industria TI-OT.

* Se supone que no existe un proceso automatizado de desactivación de cuentas al finalizar un contrato, y que para ello se depende entonces de una gestión manual a través de Recursos Humanos y TI.

* Se supone que la segregación de funciones (SoD) de SAP para la creación y la aprobación de pagos a proveedores no está completamente configurada de manera sistémica.

* Se supone que la información geológica y de reservas no está organizada ni restringida por rol de manera granular.

* Se supone que los cambios de configuración en PLCs/RTUs en campo no están sujetos a un registro formal de aprobación (change log).

## Activos o procesos identificados

* Red de automatización y control industrial (OT/SCADA) de refinerías y oleoductos — infraestructura.

* Proceso de administración de cuentas y accesos remotos a la red OT (empleados, ingenieros y contratistas) — proceso.

* Módulo financiero de SAP ERP (pagos a proveedores, nómina, liquidación de regalías) — aplicación.

* Base de datos de información geológica y de reservas (estudios sísmicos, datos de pozos) — información.

* Proceso de gestión de cambios en la configuración de PLCs/RTUs en campo — proceso.

## Matriz de riesgos

| ID | Activo o proceso | Amenaza | Vulnerabilidad | Riesgo | Prob. | Impacto | Nivel | Control actual / evidencia | Control propuesto | Justificación |
| ----- | :---- | :---- | :---- | :---- | ----- | ----- | ----- | :---- | :---- | :---- |
| **R-01** | Red OT/SCADA de refinerías | Atacante externo (p. ej. grupo de ransomware industrial) que explota la conexión remota de un contratista de mantenimiento | La VPN de contratistas no cuenta con autenticación multifactor ni segmentación de red hacia la zona OT | Un atacante podría obtener acceso a la red de control industrial a través de la conexión remota de un contratista y detener la operación de una refinería | 4 | 5 | **20** | No se encontró evidencia documentada de MFA ni de segmentación tipo Purdue para accesos remotos de terceros | Implementar MFA obligatorio y segmentación de red (DMZ) para todas las conexiones remotas de contratistas a la red OT, con revisión trimestral de accesos activos | Infraestructura crítica nacional; una interrupción prolongada afecta el suministro de combustibles del país |
| **R-02** | Proceso de administración de cuentas OT | Un excontratista o exempleado que conserva una cuenta de acceso privilegiado a la red OT | No existe un proceso formal de revocación de accesos al finalizar contratos de mantenimiento | Un excontratista podría ingresar a la red de control y modificar parámetros operativos de una planta porque su cuenta sigue activa después de finalizado el contrato | 3 | 5 | **15** | No hay evidencia de una auditoría periódica de cuentas asociadas a contratos vencidos | Desactivación automática de cuentas al vencimiento del contrato en el sistema de gestión de identidades, y auditoría mensual de cuentas activas sin contrato vigente | Acceso privilegiado a un sistema crítico; la baja manual actual depende de la coordinación entre áreas |
| **R-03** | Módulo financiero de SAP (pagos a proveedores) | Un empleado interno del área financiera con conflicto de interés | Segregación de funciones insuficiente: el mismo usuario puede crear y aprobar pagos a proveedores | Un usuario interno podría registrar y aprobar un pago a un proveedor ficticio porque el sistema no separa las funciones de creación y aprobación de pagos | 2 | 4 | **8** | No se encontró evidencia de una matriz de segregación de funciones (SoD) configurada en SAP | Configurar controles de SoD en SAP y revisión trimestral de transacciones críticas de pagos por auditoría interna | Afecta el cumplimiento de SOX (Sección 404\) y expone a Ecopetrol a riesgo de fraude financiero |
| **R-04** | Base de datos geológica y de reservas | Un competidor o actor externo interesado en información estratégica | El acceso a los datos sísmicos y de reservas no está restringido por rol o necesidad de conocer | Información geológica estratégica podría filtrarse a un tercero porque distintas áreas tienen acceso sin un control granular | 2 | 4 | **8** | No hay evidencia de clasificación de la información ni de control de acceso basado en roles para esta base de datos | Clasificar la información geológica como confidencial, implementar control de acceso basado en roles (RBAC) y auditar las consultas trimestralmente | Pérdida de ventaja competitiva y de valor comercial estratégico para la compañía |
| **R-05** | Gestión de cambios en PLCs/RTUs de campo | Error humano o modificación no autorizada durante una labor de mantenimiento | No existe un proceso formal de aprobación y registro de cambios de configuración en campo | Un cambio no autorizado o mal ejecutado en la configuración de un PLC podría provocar una parada no programada o una condición insegura en la planta | 3 | 5 | **15** | No se encontró evidencia de un registro de cambios (change log) para configuraciones de campo | Implementar un proceso formal de gestión de cambios con aprobación previa y registro de cada modificación en PLCs/RTUs, alineado con ITIL | Afecta directamente la continuidad operativa y la seguridad física de la planta |

## Priorización

Procurar el enlace entre la red de control y automatización industrial (OT/SCADA) de una refinería-oleoducto \-- infraestructura.

Ejecutar el proceso de administración de políticas de cuentas de acceso remoto a la red OT (empleados, ingenieros y contratistas) \-- proceso.

Aplicar el módulo financiero del SAP ERP (pagos a proveedores, nómina, liquidación de regalías) \-- aplicación.

Consolidar la base de datos de información geológica e información de reservas (estudios sísmicos, datos de pozos) \-- información.

Implementar un proceso de gestión de cambios en la configuración de PLCs/RTUs en campo \-- proceso.


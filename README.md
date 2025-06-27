# INFORME DE AUDITORÍA TÉCNICA  
**Despliegue de WordPress usando Vagrant y Chef**

## 1. INFORMACIÓN GENERAL

- **Nombre del estudiante:** Justin Zinedine ZEVALLOS PURCA  
- **Curso:** Auditoría de Sistemas  
- **Proyecto:** Despliegue de WordPress con Vagrant y Chef  
- **Fecha:** Junio 2025  
- **Repositorio GitHub:** [https://github.com/JustinZP/AS_U3_EXAMEN_PRACTICO.git](https://github.com/JustinZP/AS_U3_EXAMEN_PRACTICO.git)

---

## 2. OBJETIVO DE LA AUDITORÍA

Verificar la correcta automatización del despliegue de una infraestructura compuesta por tres máquinas virtuales: servidor de base de datos, servidor web con WordPress y servidor proxy, utilizando tecnologías como Vagrant y Chef. Se busca garantizar la trazabilidad, reproducibilidad y funcionamiento final de la aplicación WordPress.

---

## 3. ALCANCE DE LA AUDITORÍA

- Revisión del archivo `Vagrantfile` y recetas Chef.  
- Correcta creación y estado de las VMs: `wordpress`, `database`, `proxy`.  
- Ejecución sin errores de las recetas Chef.  
- Funcionamiento final de WordPress accesible desde navegador.  
- Análisis de configuración respaldado por evidencias.  

---

## 4. TECNOLOGÍAS UTILIZADAS

| Tecnología       | Versión               | Función                                      |
|------------------|------------------------|----------------------------------------------|
| Vagrant          | 2.3.7 o superior       | Provisión y control de máquinas virtuales    |
| VirtualBox       | 7.0 o superior         | Entorno de virtualización de VMs             |
| Chef             | 17.x                   | Automatización de configuración              |
| Ruby             | 2.5 o superior         | Requisito para ejecutar Vagrant y Chef       |
| Sistema Base     | Ubuntu 20.04 / CentOS 8| Sistema operativo de las VMs                 |

---

## 5. DETALLE DE LAS VERIFICACIONES

### 5.1. VMs desplegadas

- Se desplegaron 3 VMs:
  - `Chef_Vagrant_Wp_wordpress`
  - `Chef_Vagrant_Wp_database`
  - `Chef_Vagrant_Wp_proxy`

- Verificación mediante `vagrant status`.

📎 Ver: `evidencias/vm_virtualbox.png`, `evidencias/vagrant_status_terminal.png`

---

### 5.2. Vagrantfile

- Define 3 VMs con IPs privadas en el rango `192.168.56.0/24`.  
- Usa provisioners `chef_solo` para cada máquina.  
- Las recetas están organizadas por función.  

📎 Ver: `evidencias/fragmentos_codigo.png`

---

### 5.3. Ejecución de recetas Chef

- Se instalaron y configuraron servicios: **NGINX**, **PHP**, **MySQL**, **WordPress**.  
- Evidencia de ejecución de `service[nginx] restart`.  
- Sin errores en logs de consola.

📎 Ver: 
- `evidencias/Ejecución de recetas Chef.png`  
- `evidencias/Ejecución de recetas Chef_2.png`  
- `evidencias/Ejecución de recetas Chef_3.png`

---

### 5.4. Acceso a WordPress

- WordPress accesible en navegador: [http://192.168.56.2/](http://192.168.56.2/)  
- Se muestra interfaz de instalación correctamente.

📎 Ver: `evidencias/despliegue_wordpress.png`

---

## 6. CONCLUSIONES

- Las 3 VMs fueron desplegadas correctamente.  
- Las recetas Chef funcionaron sin errores.  
- WordPress es accesible desde navegador.  
- Se cumple el principio de **Infraestructura como Código**.  
- Entorno reproducible en otros equipos con misma configuración.

---

## 7. RECOMENDACIONES

- Documentar cada receta Chef para mantenimiento.  
- Agregar script de verificación post-provisionamiento.  
- Utilizar variables para mejorar reutilización en `Vagrantfile`.

---

## 8. EVIDENCIAS Y ANEXOS

| Anexo | Descripción                                                               |
|-------|---------------------------------------------------------------------------|
| 1     | Acceso a WordPress – `despliegue_wordpress.png`                          |
| 2     | Ejecución de recetas Chef – `Ejecución de recetas Chef.png`              |
| 3     | Logs adicionales Chef – `Ejecución de recetas Chef_2.png`                |
| 4     | Reinicio NGINX por Chef – `Ejecución de recetas Chef_3.png`              |
| 5     | Vagrantfile máquina database – `fragmentos_codigo_database.png`          |
| 6     | Vagrantfile máquina proxy – `fragmentos_codigo_proxy.png`                |
| 7     | Vagrantfile máquina wordpress – `fragmentos_codigo_wordpress.png`        |
| 8     | Estado de VMs – `vagrant_status_terminal.png`                            |
| 9     | Visualización en VirtualBox – `vm_virtualbox.png`                        |

---

> **Repositorio**: [https://github.com/JustinZP/AS_U3_EXAMEN_PRACTICO.git](https://github.com/JustinZP/AS_U3_EXAMEN_PRACTICO.git)

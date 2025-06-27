# INFORME DE AUDITORÍA DEL DESPLIEGUE DE WORDPRESS USANDO VAGRANT Y CHEF

## 1. INFORMACIÓN GENERAL
- **Nombre del Proyecto:** Despliegue de WordPress usando Vagrant y Chef
- **Curso:** Auditoría de Sistemas
- **Estudiante:** [Justin Zinedine Zevallos Purca]
- **Fecha:** Junio 2025

## 2. OBJETIVO DE LA AUDITORÍA
Verificar el despliegue automatizado de una arquitectura compuesta por tres máquinas virtuales (proxy, wordpress, database) utilizando tecnologías de virtualización, automatización de infraestructura y buenas prácticas de infraestructura como código.

## 3. ALCANCE
Se audita el entorno local, VirtualBox y Vagrant, el archivo `Vagrantfile`, las recetas Chef y el funcionamiento correcto de WordPress al finalizar el despliegue.

## 4. HALLAZGOS Y VERIFICACIONES

### 4.1 Infraestructura desplegada
- Se levantaron 3 VMs: `wordpress`, `database`, `proxy`.
- Verificado con `vagrant status` (ver imagen en `/evidencias/vagrant_status_terminal.png`).

### 4.2 Configuración del archivo Vagrantfile
- Define redes privadas en 192.168.56.X
- Se usaron box `ubuntu/bionic64` o `generic/centos8`
- Las recetas están correctamente asociadas a cada máquina.

### 4.3 Automatización con Chef
- Recetas personalizadas para instalar `nginx`, `mysql`, `php`, y WordPress.
- Se reinician servicios tras cambios (`nginx restart` verificado en consola).

### 4.4 Funcionamiento de la aplicación
- WordPress accesible en `http://192.168.56.2/`
- Funcionamiento verificado en navegador (ver imagen `/evidencias/despliegue_wordpress.png`).

## 5. CONCLUSIONES
- ✅ El entorno fue desplegado correctamente con Vagrant y Chef.
- ✅ Se cumplió con el principio de infraestructura como código.
- ✅ WordPress funciona y es accesible desde navegador.
- ✅ Las evidencias respaldan cada paso de auditoría.

## 6. RECOMENDACIONES
- Implementar pruebas automáticas post-despliegue para verificar estado de servicios.
- Documentar en mayor detalle las recetas y parámetros personalizables.

## 7. EVIDENCIAS
Ver carpeta `/evidencias/`.


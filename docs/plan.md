# Plan de Desarrollo

## Meta

Crear un custom component de Home Assistant que permita visualizar entidades basicas de una instancia local de Home Assistant en una pagina propia, iniciando con el nivel del tanque de gas.

## Alcance Inicial

- Mantener una integracion instalable como `custom_component`.
- Permitir configurar la integracion desde la UI de Home Assistant.
- Leer una entidad existente de Home Assistant local.
- Mostrar el nivel del tanque de gas como primera entidad objetivo.
- Preparar una pagina o vista basica para consultar entidades seleccionadas.

## Supuestos

- La entidad del tanque de gas ya existe en Home Assistant local.
- La primera version puede trabajar con una entidad configurada manualmente.
- La integracion se probara primero en un entorno local de Home Assistant.
- No se requiere aun publicar la integracion en HACS.

## Fases

### Fase 1: Estructura Base

- Crear `manifest.json`.
- Crear `__init__.py`.
- Crear `config_flow.py`.
- Confirmar que Home Assistant detecta la integracion.

### Fase 2: Configuracion Basica

- Solicitar nombre de la integracion desde el config flow.
- Agregar campo para capturar el `entity_id` del tanque de gas.
- Guardar la configuracion como config entry.
- Evitar configuraciones duplicadas cuando aplique.

### Fase 3: Lectura de Entidad

- Leer el estado de la entidad configurada desde `hass.states`.
- Validar que la entidad exista.
- Manejar errores basicos cuando la entidad no este disponible.
- Registrar datos minimos en `hass.data`.

### Fase 4: Visualizacion Basica

- Definir el mecanismo de visualizacion dentro de Home Assistant.
- Mostrar el valor actual del tanque de gas.
- Mostrar metadatos basicos de la entidad si estan disponibles.
- Preparar la estructura para agregar mas entidades en el futuro.

### Fase 5: Prueba Local

- Instalar el componente en una instancia local de Home Assistant.
- Reiniciar Home Assistant.
- Agregar la integracion desde la UI.
- Configurar el `entity_id` del tanque de gas.
- Confirmar que el valor se puede consultar o visualizar.

## Entidad Inicial Objetivo

- Tipo: sensor o entidad compatible existente en Home Assistant.
- Uso esperado: nivel del tanque de gas.
- Dato requerido: `entity_id` exacto de Home Assistant, por ejemplo `sensor.tanque_gas`.

## Pendientes por Definir

- `entity_id` real del tanque de gas.
- Si la visualizacion sera una pagina propia, panel, dashboard card, sensor agregado o servicio.
- Si se requiere autenticacion externa o solo acceso interno a entidades ya registradas en Home Assistant.
- Unidades esperadas para el nivel del tanque: porcentaje, litros, kilogramos u otra unidad.

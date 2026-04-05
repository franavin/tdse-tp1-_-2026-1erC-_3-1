## Parking Ticket Dispenser Machine (Entry) - Módulo de Actuador
**-Módulo de código C:** Temporizado  
**-Período de escrutinio:** 1 ms
***************************************************************************************************************************************************************************************************************************
## 1. Descripción del Modelo

***************************************************************************************************************************************************************************************************************************
## 2. Estados
* **`ST_ACT_IDLE`**: 
* **`ST_ACT_MOVING`**:

## 3. Eventos
* **`EV_ACT_OPEN`**:
* **`EV_ACT_CLOSE`**:
* **`EV_SYS_READY`**:

## 4. Variables de Control
* **`tick`**: Variable temporizadora de cuenta regresiva.
* **`DEL_LED_BARRERA_MAX`**: Es una constante que define el tiempo en que la barrera tarda en abrir/cerrar.

## 5. Acciones

### Acciones Internas
* **`tick = DEL_BTN_BARRERA_MAX`**: Inicializa la variable de control.
* **`tick--`**: Decrementa la variable de control.
* **`LED_ON`**:
* **`LED_OFF`**:  

### Acciones Externas

* **`raise EV_SYS_READY`**: Emite la señal al sistema
* 
### Actuator Statechart - State Transition Table

| Current State | Event | [Guard] | Next State | Actions |
| :--- | :--- | :--- | :--- | :--- |
| ST_ACT_IDLE  |EV_ACT_CLOSE |  | ST_ACT_IDLE | |
| | EV_ACT_OPEN |  | ST_ACT_OPENING |LED_ON; tick = DEL_LED_BARRERA_MAX|
| ST_ACT_OPENING | | tick>0 |ST_ACT_OPENING | tick--|
|  | |tick==0  | ST_ACT_UP|raise EV_SYS_READY |
|ST_ACT_UP  |EV_ACT_CLOSE | |ST_ACT_CLOSING  | tick = DEL_LED_BARRERA_MAX|
|  ST_ACT_CLOSING| |tick>0  |ST_ACT_CLOSING | tick--|
|  | |tick==0  | ST_ACT_IDLE|LED_OFF; raise EV_SYS_READY |

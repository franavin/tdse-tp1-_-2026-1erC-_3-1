## Parking Ticket Dispenser Machine (Entry) - Módulo de Actuador
**-Módulo de código C:** Temporizado  
**-Período de escrutinio:** 1 ms
***************************************************************************************************************************************************************************************************************************
## 1. Descripción del Modelo

***************************************************************************************************************************************************************************************************************************
## 2. Eventos

* **`EV_BTN_XX_UP`**: 
* **`EV_BTN_XX_DOWN`**:

## 3. Variables de Control



## 4. Acciones

### Acciones Internas



### Acciones Externas
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

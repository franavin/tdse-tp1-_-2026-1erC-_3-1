## Parking Ticket Dispenser Machine (Entry) - Módulo de Sensores
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




### System Statechart - State Transition Table

| Current State | Event | [Guard] | Next State | Actions |
| :--- | :--- | :--- | :--- | :--- |
| ST_SYS_CLOSED  | EV_SYS_XX_DOWN | |ST_SYS_OPENING  |raise EV_ACT_OPEN |
| ST_SYS_OPENING | EV_SYS_READY | |ST_SYS_OPEN | |
| ST_SYS_OPEN | EV_SYS_XX_UP | |ST_SYS_CLOSING |raise EV_ACT_CLOSE |
| ST_SYS_CLOSING| EV_SYS_READY | |ST_SYS_CLOSED| |

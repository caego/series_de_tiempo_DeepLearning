# Modelos clásicos

## Tipos de modelos de enfoque clasico

### Modelos Lineales
Suponen una relación aditiva y proporcional entre los valores pasados y presentes, con efectos constantes en el tiempo
- AR(p)
- MA(q)
- ARMA(p,q)
- ARIMA (p,d,q)
- SARIMA

**Características:**

- Forma funcional paramétrica
- Relación con rezagos lineal y aditiva
- Media Lineal
- Homocedásticos
- Estacionario (una vez diferenciada, si es necesario)

### Modelos No Lineales
Introducen dependencias dinámicas y asimétricas, permitiendo que los efectos de los choques pasados varíen según el estado del sistema o magnitud
- TARCH
- Threshold models (TAR, SETAR)
- Regime-Switching
- Modelos caóticos

**Características:**

- Forma funcional NO paramétrica
- Relación con rezagos dependen de sistema o magnitud de choques
- Media posiblemente no lineal
- Heterocedásticos
- Puede exhibir cambios de régimen

## Modelos lineales: AR

Un proceso AR(p) describe el valor actual de la serie como una combinación lineal de sus propios valores pasados y un término de error

$ r_t = \phi _0 + \phi _1 r_{t-1} + ... + \phi _p r_{t-p} + a_t $

Donde $a_t$ es un ruido blanco.<br>

**Recordar:**
- *Ruido blanco en los residuales es que su media es cero y su varianza constante, y covarianza cero.*
- *En una serie estacionaria con estructura autorregresiva, la ACF decae gradualmente (de forma exponencial u oscilatoria). Si la ACF permanece alta y decae muy lentamente, esto sugiere no estacionariedad y puede requerirse diferenciación antes de modelar.<br>*
- *La función de autocorrelación parcial (PACF) es útil para identificar el orden p en un modelo AR(p), ya que presenta un corte en el rezago p cuando la serie es estacionaria.<br>
- *Un orden muy alto, no es candidato a trabajarse de forma autorregresiva.<br>*
- Usa un AR cuando la serie es estacionaria, la ACF decae gradualmente y la PACF muestra un corte claro en p.<br>
- *Recordar que Una serie de tiempo AR(p) es estacionaria si las raíces del polinomio característico:  $ 1 - \phi _1 z  - \phi _2 z^2 - ... - \phi _p z^p $ están fuera del círculo unitario, es decir: $ |z_i| > 1 $*

El modelo AR captura la persistencia temporal de la serie, describiendo cómo los shocks pasados se transmiten gradualmente en el tiempo.

## Modelos lineales: MA

Un proceso MA(q) representa $r_i$ como una combinación lineal de choques actuales y pasados.


$ r_t = \mu + a_t - \phi _1 a_{t-1} - ... - \phi _q a_{t-q} $<br>
donde $ a_t = \mu - y_t $

Estos modelos son siempre estacionarios y capturan dependencias de corto plazo.
La función de autocorrelación ACF se corta en el rezago q.

### Estacionariedad
Los modelos MA son siempre estacionarios.
### invertivilidad
- Debe ser invertible para garantizar una representación única y estable.
- Esto pernmite expresar el modelo MA como un proceso AR($\infty$)
### Estructura de autocorrelación
- La ACF del modelo MA(q) se corta en el rezago q
- La PACF disminuye gradualmente

Los errores estimados deben comportarse como ruido blanco

## Modelos lineales: Extensiones
### ARIMA
Generalizan el enfoque al permitir series no estacionarias mediante diferenciación.<br>
un modelo ARIMA(p,d,q) modela una serie que se vuelve estacionaria tras diferenciarla d veces.<br>
$\phi _p (B) (1-B)^d y_t = \theta _q (B) {\varepsilon_t}$

| Parámetro | Significado | Efecto |
| --- | --- | --- |
| p | Orden del término autoregresivo | Define cuantos valores del pasado afectan el presente - Captura persistencia |
| d | Grado de diferenciación | Controla la eliminación de tendencia - hace estacionaria la serie|
| q | Orden del término de media móvil | Cuantos errores pasados influyen en el presente - captura chocks de corto plazo |


### SARIMA
Permite capturar tanto los patrones no estacionarios como los comportamientos estacionales de una serie de tiempo.<br>
Un modelo SARIMA (p,d,q)(P,D,Q) Añade la dinámica estacional.<br>
$\phi _P (B^s) \phi _p (B) (1-B)^d (1-B^s)^D y_t = \theta _Q (B^s) \theta _q (B) {\varepsilon_t}$

| Tipo | Orden | Significado | Que captura | Intuición |
| --- | --- | --- | --- | --- |
| AR(p) | Autorregresivo no estacional | Relación con observaciones pasadas | Memoria reciente | Inercia |
| I(d) | Diferenciación no estacional | Elimina tendencia general | Sorpresas recientes | Ajuste fino |
| MA(q) | Media móvil no estacional | Corrige correlación de errores | Tendencia | Nivel cambiante |
| SAR(P) | Autorregresivo escacional | Dependencia de observaciones cada (s) periodos |  Memoria estacional | Repetición anual/mensual |
| SI(D) | Diferenciación estacional | Elimina patrón periódico | Shoks estacionales | Perturbaciones periódicas |
| SMA(Q) | Media móvil estacional | Corrige correlación de errores cada (s) pasos | Tendencia estacional | Cambio en ciclos |

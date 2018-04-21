# Sensoren

Die Sensoren sind als [Trait][sensor-trait] definiert.

## Funktionen des Traits

- value (Direktwert)
- average (Mittelwert)
- update (Update der Werte)

Die konkreten Sensortypen (Analog 4-20mA, CO/NO2 Modbus Kombisensor) implementieren dann diesen Sensor [Trait][sensor-trait].

Jedem Messwert ist ein Zeitstempel zugeordnet. Dieser wird bei der Mittelwert-
bildung verwendet.

Jede Sensor Instanz speichert die Messwerte der letzten 60 Minuten. Ältere Mess-
werte werden verworfen.


## Sensortypen
### RA-GAS CO Sensor Modbus (CO/NO2 Kombisensor mit Modbus Interface)
### RA-GAS NO2 Sensor Modbus (CO/NO2 Kombisensor mit Modbus Interface)
### 4-20mA Analog Sensor an MR-CI4 (Metz Konnect Modbus Interface)
### Simmulation Sensor 15Minuten Mittelwert (15min 0, 15min max) "___|||___|||___"
### Simmulation Sensor 30Minuten Mittelwert (30min 0, 30min max) "______||||||______||||||______"
### Sägezahn "__/\__/\__/\__"
### Tablou "___/||\___/||\___"
### Random "__|\___/|_/||||__"





# Links

- [https://kliemann-service-gmbh.github.io/xmz-server/xmz_server/server/sensor/trait.Sensor.html][sensor-trait]



[sensor-trait]: https://kliemann-service-gmbh.github.io/xmz-server/xmz_server/server/sensor/trait.Sensor.html

# Web und JSON API

`GET` Requests die von der Web/ JSON-API unterstützt werden:

## JSON API

Die JSON API ist unter der URL `/api/` erreichbar

* `GET /api/ HTTP/1.1` - Index liefert kompletten Server
  * <http://localhost:8000/>
* `GET /api/sensors HTTP/1.1` - Sensoren Index, liefert alle Sensoren des Servers
  * <http://localhost:8000/sensors>
* `GET /api/sensor/<id> HTTP/1.1` - Liefert den Sensore mit der `<id>`, oder 404 wenn dieser nicht exisitert
  * <http://localhost:8000/sensor/0>
* `GET /api/sensor/<id>/messzellen HTTP/1.1` - Messzellen Index, liefert alle Messzellen des Sensors
  * <http://localhost:8000/sensor/0/messzellen>
* `GET /api/sensor/<sensor_id>/messzelle/<id> HTTP/1.1` - Liefert die Messzelle mit der `<id>` oder 404 wenn diese nicht existiert
  * <http://localhost:8000/sensor/0/messzelle/0>

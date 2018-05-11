# Web und json API

`GET` Requests die von der Web/ json-API unterstützt werden:

* `GET /` - Index liefert kompletten Server als JSON
  * <http://localhost:8000/>
* `GET /sensors` - Sensoren Index, liefert alle Sensoren des Servers
  * <http://localhost:8000/sensors>
* `GET /sensor/<id>` - Liefert den Sensore mit der `<id>`, oder 404 wenn dieser nicht exisitert
  * <http://localhost:8000/sensor/0>
* `GET /sensor/<id>/messzellen` - Messzellen Index, liefert alle Messzellen des Sensors
  * <http://localhost:8000/sensor/0/messzellen>
* `GET /sensor/<sensor_id>/messzelle/<id>` - Liefert die Messzelle mit der `<id>` oder 404 wenn diese nicht existiert
  * <http://localhost:8000/sensor/0/messzelle/0>

# cockpit-temperature-plugin
Cockpit Temperature Plugin using [smoothie-charts](http://smoothiecharts.org)

To intall, as described in [Cockpit docs](https://cockpit-project.org/blog/creating-plugins-for-the-cockpit-user-interface.html) simply put the files in ```/usr/share/cockpit``` for the plugin to be available for all system useres **or** in a spesific user folder under ```~/.local/share/cockpit```

Run:
```
dnf install lm_sensors
```
then:
```
sensors-detect
```
then:
```
sensors
```
example output of sensors:
```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +63.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +62.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +63.0°C  (high = +100.0°C, crit = +100.0°C)

nvme-pci-3c00
Adapter: PCI adapter
Composite:    +47.9°C  (low  = -273.1°C, high = +76.8°C)
                       (crit = +78.8°C)
Sensor 1:     +47.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +52.9°C  (low  = -273.1°C, high = +65261.8°C)
```

On line 13 of temperature.js, change "Core 1" to the sensor you want monitored in cockpit.

```js
var proc = cockpit.script("sensors | grep 'Core 1' | awk '{print $3}'");
```

screenshots:
![Fedora](https://github.com/dannygils/cockpit-temperature-plugin/blob/master/screenshots/fedora.png?raw=true)



## ПИД регулятор для ESP8266

[![micropython](https://user-images.githubusercontent.com/13176091/53680744-4dfcc080-3ce8-11e9-94e1-c7985181d6a5.png)](https://micropython.org/)

За основу данной библиотеки была взят [simple-pid](https://github.com/m-lundberg/simple-pid/blob/master/README.md#simple-pid).

Библиотека [simple-pid](https://github.com/m-lundberg/simple-pid/blob/master/README.md#simple-pid) была адаптирована для работы с микроконтроллерами ESP8266
В основе библиотеки лежит руководство [Brett Beauregards](http://brettbeauregard.com/blog/2011/04/improving-the-beginners-pid-introduction/).

[Документация](https://simple-pid.readthedocs.io/en/latest/simple_pid.html#module-simple_pid.PID) для ПИД контроллера

***Пример использования:***
```python
from esp_pid import PID
pid = PID(1, 0.1, 0.05, setpoint=1)

# у нас есть система которую хотим контролировать
v = controlled_system.update(0)

while True:
    # расчет погрешности ПИД контроллером
    control = pid(v)
    
    # применение к контролируемой системе расчитанной ПИД контроллером новой погрешности
    v = controlled_system.update(control)
```

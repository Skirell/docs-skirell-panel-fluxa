Тип sensor (Датчики)
====================

.. image:: /images/sensor/blocks.png

Блок sensor отображает данные с датчиков. Подтипов нет. 

Параметры:

* :ref:`sensor-param_1`: название датчика (например: ``Температура``).
* :ref:`sensor-measure`: единица измерения (например: ``°C``).
* :ref:`sensor-min`: минимальное значение(датчика) для цветового индикатора.
* :ref:`sensor-stage_1`: первая граница для цветового индикатора.
* :ref:`sensor-stage_2`: вторая граница для цветового индикатора.
* :ref:`sensor-max`: максимальное значение(датчика) для цветового индикатора.
* :ref:`sensor-color_1`: цвет индикатора для значений ниже stage_1 (``min`` > ``color_1`` < ``stage_1``).
* :ref:`sensor-color_2`: цвет индикатора для значений между stage_1 и stage_2 (``stage_1`` > ``color_2`` < ``stage_2``).
* :ref:`sensor-color_3`: цвет индикатора для значений выше stage_2 (``stage_2`` > ``color_3`` < ``max``).
* :ref:`sensor-state_topic`: MQTT-топик обратной связи для получения данных.


Полный пример датчиков с верхного изображения:
    * :ref:`sensor-full_example`

.. raw:: html

    <br/><br/>
    <br/><br/>


.. _sensor-full_example:
Полный пример датчиков
---------------------------------
Пример::

    {
        "screens": [
            {
                "page": 1,
                "blocks": [
                    {
                    "block": 1,
                    "type": "sensor",
                    "data": {
                        "param_1": "Температура",
                        "measure": "°C",
                        "min": "10",
                        "stage_1": "20",
                        "stage_2": "30",
                        "max": "40",
                        "color_1": "color_blue",
                        "color_2": "color_green",
                        "color_3": "color_red",
                        "state_topic": "panel/sensor/1/state"
                    }
                    },
                    {
                    "block": 2,
                    "type": "sensor",
                    "data": {
                        "param_1": "Влажность",
                        "measure": "%",
                        "min": "20",
                        "stage_1": "40",
                        "stage_2": "60",
                        "max": "80",
                        "color_1": "color_green",
                        "color_2": "color_yellow",
                        "color_3": "color_red",
                        "state_topic": "panel/sensor/2/state"
                    }
                    },
                    {
                    "block": 3,
                    "type": "sensor",
                    "data": {
                        "param_1": "Углекислый газ",
                        "measure": "ppm",
                        "min": "400",
                        "stage_1": "800",
                        "stage_2": "1200",
                        "max": "2000",
                        "color_1": "color_green",
                        "color_2": "color_yellow",
                        "color_3": "color_red",
                        "state_topic": "panel/sensor/3/state"
                    }
                    },
                    {
                    "block": 4,
                    "type": "sensor",
                    "data": {
                        "param_1": "Качество воздуха",
                        "measure": "ppb",
                        "min": "0",
                        "stage_1": "200",
                        "stage_2": "500",
                        "max": "1000",
                        "color_1": "color_green",
                        "color_2": "color_yellow",
                        "color_3": "color_red",
                        "state_topic": "panel/sensor/4/state"
                    }
                    }
                ]
            }
        ]
    }
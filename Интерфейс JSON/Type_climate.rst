Тип climate (Климат)
====================

.. image:: /images/climate/main.png

Блок ``climate`` используется для управления различными климатическими устройствами. Поддерживает два типа устройств. При кратковременном нажатии на блок открывается страница его настроек. Общие параметры:

* :ref:`climate-param_1` — назначение блока (например, тип устройства: «Тёплый пол», «Увлажнитель»).
* :ref:`climate-param_2` — локация или контекст использования (например, «Кухня», «Гостиная»).
* :ref:`climate-setting_name` — название устройства в настройках.
* :ref:`climate-icon` — иконка, отображаемая на блоке.
* :ref:`climate-min_target` - минимальное значение целевой (заданной) температуры.
* :ref:`climate-max_target` - максимальное значение целевой (заданной) температуры.
* :ref:`climate-measure` - единица измерения (например: ``°C``).
* :ref:`climate-color` - цвет индикатора термостата в активном состоянии (кроме режима "Выключено").
* :ref:`climate-variant` — объект с параметрами выбранного варианта устройства.
* :ref:`climate-variant_type` — тип устройства (вариант функциональности):
   * :ref:`climate_variant_thermostat` — базовый термостат с режимами "Включено"/"Выключено", с возможностью подключения до трёх датчиков.
   * :ref:`climate_variant_cond` — расширенный термостат с поддержкой от 2 до 5 режимов работы и от 0 до 5 режимов вентиляции.

Полный пример климата с верхнего изображения:
    * :ref:`climate-full_example`

.. raw:: html

    <br/><br/>
    <br/><br/>


Детальный разбор параметров:
----------------------------

.. _climate-param_1:
param_1
*******
   Используется для изменения текста в самом блоке, например, чтобы указать, что это «Тёплый пол» или «Увлажнитель». Может применяться и в других целях.

   :имя поля: ``param_1``
   :тип объекта: ``String``
   :наличие значения: Может быть пустым
   :ограничение строки: 9 символов
   :пример-1: ``"param_1":"Торшеры"``
   :пример-2: ``"param_1":"Освещение"``
   :пример-3: ``"param_1":""``

.. image:: /images/climate/param_1.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _climate-param_2:
param_2
*******
   Используется для изменения текста в самом блоке. Например, позволяет уточнить, где будет находиться данное климатическое устройство. Если панель установлена в конкретной комнате, а все климатические устройства относятся к ней, это поле можно оставить пустым и написать значение из ``param_1`` сюда.

   :имя поля: ``param_2``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: 11 символов
   :пример-1: ``"param_2":"Спальня"``
   :пример-2: ``"param_2":"Прихожая"``
   :пример-3: ``"param_2":"Торшеры"``

.. image:: /images/climate/param_2.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _climate-setting_name:
setting_name
************
   Используется для изменения заголовка на странице настроек. Обычно можно продублировать значение из ``param_2``, но иногда бывают ситуации когда в блоке пришлось написать сокращенно, то в настройках можно написать полностью.

   :имя поля: ``setting_name``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: 14 символов
   :пример-1: ``"setting_name":"Торшеры"``
   :пример-2: ``"setting_name":"Точки"``
   :пример-3: ``"setting_name":"Подсветка"``

.. image:: /images/climate/setting_name.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _climate-icon:
icon
****
   Используется для изменения иконки в самом блоке.

   :имя поля: ``icon``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Стандартный unicode
   :пример-1: ``"icon":"\uDB81\uDF64"`` - иконка 
   :пример-2: ``"icon":"\uDB86\uDCDE"`` - иконка
   :пример-3: ``"icon":"\uDB84\uDC51"`` - иконка

.. image:: /images/climate/icon.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _climate-min_target:
min_target
****
   Используется для изменения иконки в самом блоке.

   :имя поля: ``min_target``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"min_target":"15"``


.. _climate-max_target:
max_target
****
   Используется для изменения иконки в самом блоке.

   :имя поля: ``max_target``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"max_target":"30"``


.. _climate-measure:
measure
*******
   Используется для изменения текста единицы измерения в самом блоке, например, чтобы указать, что это единица измерения «°C» или «%». Может применяться и в других целях.

   :имя поля: ``measure``
   :тип объекта: ``String``
   :наличие значения: Может быть пустым
   :ограничение строки: 5 символов
   :пример-1: ``"measure":"°C"``
   :пример-2: ``"measure":"%"``

.. _climate-color:
measure
*******
   Используется как цвет для активного состояния (все кроме режима ВЫКЛ), в самом блоке и на странице настроек(кроме подтипа ``climate_variant_cond``).

   :имя поля: ``color``
   :тип объекта: ``String``
   :наличие значения: Может быть пустым
   :ограничение строки: 5 символов
   :пример-1: ``"color":"°C"``
   :пример-2: ``"color":"%"``


.. image:: /images/climate/measure.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _climate-full_example:
Полный пример климата
---------------------------------
Пример::

    {
        "screens": [{
            "page": 1,
            "blocks": [
                {
                    "block": 1,
                    "type": "climate",
                    "data": {
                        "param_1": "Конд-ер",
                        "param_2": "Зал",
                        "setting_name": "Кондиционер",
                        "icon": "\uDB84\uDF52",
                        "min_target": "15",
                        "max_target": "30",
                        "off_payload": "off",
                        "measure": "°С",
                        "color": "color_red",
                        "variant_type": "climate_variant_cond",
                        "variant": {
                            "mode_command_topic": "panel/climate/1/mode_command",
                            "mode_state_topic": "panel/climate/1/mode_state",
                            "off_payload": "off",
                            "modes": {
                                "mode_1": { "icon": "\uDB86\uDCF2", "title": "Авто", "color": "color_green", "payload": "auto" },
                                "mode_2": { "icon": "\uDB80\uDE38", "title": "Обогрев", "color": "color_red", "payload": "heat" },
                                "mode_3": { "icon": "\uDB81\uDF17", "title": "Охлаждение", "color": "color_blue", "payload": "cool" },
                                "mode_4": { "icon": "\uDB81\uDD8E", "title": "Осушение", "color": "color_yellow", "payload": "dry" }
                            },
                            "currentTemp_state_topic": "panel/climate/1/currentTemp_state",
                            "targetTemp_command_topic": "panel/climate/1/targetTemp_command",
                            "targetTemp_state_topic": "panel/climate/1/targetTemp_state",
                            "fan_command_topic": "panel/climate/1/fan_command",
                            "fan_state_topic": "panel/climate/1/fan_state",
                            "fan_modes": {
                                "mode_1": { "icon": "\uDB85\uDF1D", "payload": "0" },
                                "mode_2": { "icon": "\uDB85\uDC72", "payload": "1" },
                                "mode_3": { "icon": "\uDB85\uDC73", "payload": "2" },
                                "mode_4": { "icon": "\uDB85\uDC74", "payload": "3" },
                                "mode_5": { "icon": "", "payload": "" }
                            }
                        }
                    }
                },
                {
                    "block": 2,
                    "type": "climate",
                    "data": {
                        "param_1": "Тепл. пол",
                        "param_2": "Детская",
                        "setting_name": "Теплый пол",
                        "icon": "\uDB86\uDEAF",
                        "min_target": "18",
                        "max_target": "30",
                        "measure": "°С",
                        "color": "color_red",
                        "variant_type": "climate_variant_thermostat",
                        "variant": {
                            "OnOff_command_topic": "panel/climate/2/OnOff_command",
                            "OnOff_state_topic": "panel/climate/2/OnOff_state",
                            "payload_on": "1",
                            "payload_off": "0",
                            "targetTemp_command_topic": "panel/climate/2/targetTemp_command",
                            "targetTemp_state_topic": "panel/climate/2/targetTemp_state",
                            "sensor": {
                                "sensor_main": 1,
                                "sensor_1_icon": "\uDB83\uDF55",
                                "sensor_1_measure": "°С",
                                "sensor_1_state_topic": "panel/climate/2/sensor_1_state",
                                "sensor_2_icon": "",
                                "sensor_2_measure": "",
                                "sensor_2_state_topic": "",
                                "sensor_3_icon": "",
                                "sensor_3_measure": "",
                                "sensor_3_state_topic": ""
                            }
                        }
                    }
                },
                {
                    "block": 3,
                    "type": "climate",
                    "data": {
                        "param_1": "Вент-ия",
                        "param_2": "Ванная",
                        "setting_name": "Вентиляция",
                        "icon": "\uDB80\uDE10",
                        "min_target": "0",
                        "max_target": "100",
                        "measure": "%",
                        "color": "color_green",
                        "variant_type": "climate_variant_thermostat",
                        "variant": {
                            "OnOff_command_topic": "panel/climate/3/OnOff_command",
                            "OnOff_state_topic": "panel/climate/3/OnOff_state",
                            "payload_on": "1",
                            "payload_off": "0",
                            "targetTemp_command_topic": "panel/climate/3/targetTemp_command",
                            "targetTemp_state_topic": "panel/climate/3/targetTemp_state",
                            "sensor": {
                                "sensor_main": 2,
                                "sensor_1_icon": "\uDB81\uDFE4",
                                "sensor_1_measure": "ppm",
                                "sensor_1_state_topic": "panel/climate/3/sensor_1_state",
                                "sensor_2_icon": "\uDB81\uDD8E",
                                "sensor_2_measure": "%",
                                "sensor_2_state_topic": "panel/climate/3/sensor_2_state",
                                "sensor_3_icon": "\uDB80\uDF2A",
                                "sensor_3_measure": "ppb",
                                "sensor_3_state_topic": "panel/climate/3/sensor_3_state"
                            }
                        }
                    }
                },
                {
                    "block": 4,
                    "type": "climate",
                    "data": {
                        "param_1": "Увлаж-ль",
                        "param_2": "Прихожая",
                        "setting_name": "Увлажнитель",
                        "icon": "\uDB84\uDC99",
                        "min_target": "15",
                        "max_target": "30",
                        "measure": "%",
                        "color": "color_blue",
                        "variant_type": "climate_variant_thermostat",
                        "variant": {
                            "OnOff_command_topic": "panel/climate/4/OnOff_command",
                            "OnOff_state_topic": "panel/climate/4/OnOff_state",
                            "payload_on": "1",
                            "payload_off": "0",
                            "targetTemp_command_topic": "panel/climate/4/targetTemp_command",
                            "targetTemp_state_topic": "panel/climate/4/targetTemp_state",
                            "sensor": {
                                "sensor_main": 1,
                                "sensor_1_icon": "\uDB81\uDD8E",
                                "sensor_1_measure": "%",
                                "sensor_1_state_topic": "panel/climate/4/sensor_1_state",
                                "sensor_2_icon": "",
                                "sensor_2_measure": "",
                                "sensor_2_state_topic": "",
                                "sensor_3_icon": "",
                                "sensor_3_measure": "",
                                "sensor_3_state_topic": ""
                            }
                        }
                    }
                }
            ]
        }]
    }
    
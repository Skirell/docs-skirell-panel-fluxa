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
* :ref:`climate-off_payload` - команда (сообщение), обозначающее режим "Выключено".
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
                        "icon": "󱍒",
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
                                "mode_1": {
                                "icon": "󱣲",
                                "title": "Авто",
                                "color": "color_green",
                                "payload": "auto"
                                },
                                "mode_2": {
                                "icon": "󰈸",
                                "title": "Обогрев",
                                "color": "color_red",
                                "payload": "heat"
                                },
                                "mode_3": {
                                "icon": "󰜗",
                                "title": "Охлаждение",
                                "color": "color_blue",
                                "payload": "cool"
                                },
                                "mode_4": {
                                "icon": "󰖎",
                                "title": "Осушение",
                                "color": "color_yellow",
                                "payload": "dry"
                                }
                            },
                            "currentTemp_state_topic": "panel/climate/1/currentTemp_state",
                            "targetTemp_command_topic": "panel/climate/1/targetTemp_command",
                            "targetTemp_state_topic": "panel/climate/1/targetTemp_state",
                            "fan_command_topic": "panel/climate/1/fan_command",
                            "fan_state_topic": "panel/climate/1/fan_state",
                            "fan_modes": {
                                "mode_1": {
                                "icon": "󱜝",
                                "payload": "0"
                                },
                                "mode_2": {
                                "icon": "󱑲",
                                "payload": "1"
                                },
                                "mode_3": {
                                "icon": "󱑳",
                                "payload": "2"
                                },
                                "mode_4": {
                                "icon": "󱑴",
                                "payload": "3"
                                },
                                "mode_5": {
                                "icon": "",
                                "payload": ""
                                }
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
                        "icon": "󱪯",
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
                                "sensor_1_icon": "󰽕",
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
                        "icon": "󰈐",
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
                                "sensor_1_icon": "󰟤",
                                "sensor_1_measure": "ppm",
                                "sensor_1_state_topic": "panel/climate/3/sensor_1_state",
                                "sensor_2_icon": "󰖎",
                                "sensor_2_measure": "%",
                                "sensor_2_state_topic": "panel/climate/3/sensor_2_state",
                                "sensor_3_icon": "󰌪",
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
                        "icon": "󱂙",
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
                                "sensor_1_icon": "󰖎",
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
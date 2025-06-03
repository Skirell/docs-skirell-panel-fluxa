Тип light (Свет)
=================

Блок ``light`` управляет освещением и имеет четыре подтипа. При кратковременном нажатии на блок происходит отправка команды вкл/выкл(``payload_on``, ``payload_off``), при длительном удержани происходит переход на страницу настроек блока (кроме типа ``light_variant_OnOff``). Общие параметры:

* :ref:`light-param_1` — назначение блока (например, название устройства).
* :ref:`light-param_2` — локация или контекст использования.
* :ref:`light-setting_name` — название устройства в настройках.
* :ref:`light-icon` — иконка, отображаемая на блоке.
* :ref:`light-variant_type` — название типа(варианта) настроект блока.
* :ref:`light-variant` — объект с настройками тип(варианта) блока.
   * :ref:`light-light_variant_OnOff` - тип вкл/выкл.
   * :ref:`light-light_variant_dimmer` - тип вкл/выкл, яркость.
   * :ref:`light-light_variant_temperature` - тип вкл/выкл, яркость, температура света.
   * :ref:`light-light_variant_color` - тип вкл/выкл, яркость, RGB цвет.

.. raw:: html

    <br/><br/>
    <br/><br/>

Детальный разбор параметров:
----------------------------

.. _light-param_1:
param_1
*******
   Используется для изменения текста в UI-блоке, например, чтобы указать, что это «Люстра» или «Торшер». Может применяться и в других целях.

   :имя поля: ``param_1``
   :тип объекта: ``String``
   :наличие значения: Может быть пустым
   :ограничение строки: 9 символов
   :пример-1: ``"param_1":"Освещение"``
   :пример-2: ``"param_1":"Подсветка"``
   :пример-3: ``"param_1":""``

.. image:: /images/block_param_1.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _light-param_2:
param_2
*******
   Используется для изменения текста в UI-блоке. Например, позволяет уточнить, где будет находится данное устройство-освещение. Если панель установлена в конкретной комнате, а все освещение относятся к ней, это поле можно оставить пустым и написать значение из ``param_1`` сюда.

   :имя поля: ``param_2``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: 11 символов
   :пример-1: ``"param_2":"Двор"``
   :пример-2: ``"param_2":"Спальня"``
   :пример-3: ``"param_2":"Кухня"``

.. image:: /images/block_param_2.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _light-setting_name:
setting_name
*******
   Используется для изменения текста в UI-настройках. Обычно можно продублировать значение из ``param_2``, но иногда бывают ситуации когда в блоке пришлось написать сокращенно, то в настройках можно написать полностью.

   :имя поля: ``setting_name``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: 14 символов
   :пример-1: ``"setting_name":"Люстра"``
   :пример-2: ``"setting_name":"Точки"``
   :пример-3: ``"setting_name":"Подсветка"``

.. image:: /images/setting_name.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _light-icon:
icon
*****
   Используется для изменения иконки в UI-блоке.

   :имя поля: ``icon``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Стандартный unicode
   :пример-1: ``"icon":"\uDB81\uDF64"`` - иконка 
   :пример-2: ``"icon":"\uDB81\uDF64"`` - иконка
   :пример-3: ``"icon":"\uDB81\uDF64"`` - иконка

.. image:: /images/block_icon.png
.. raw:: html

    <br/><br/>
    <br/><br/>

.. _light-variant_type:
variant_type
*****
   Используется для указания названия варианта(типа) устройства-освещения.

   :имя поля: ``variant_type``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Только заданные значения
   :варианты: ниже 
   * ``light_variant_OnOff``: вкл/выкл
   * ``light_variant_dimmer``: вкл/выкл, яркость


* ``variant_type``: Подтип (``light_variant_OnOff``, ``light_variant_dimmer``, ``light_variant_color``, ``light_variant_temperature``).
* ``variant``: Параметры подтипа, представлены ниже для каждого варианта подтипа.

Подтип light_variant_OnOff
----------------------------

Отправляет указанную команду включения/выключения на командный MQTT-топик, а также прослушивает MQTT-топик обратной связи для измения состояния элементов интерфейса.

.. image:: /images/OnOffBlocks.png

\* **Блок 1** - Состояние выкл, **Блок 2** - Состояние вкл.

Параметры ``variant``:

* OnOff_command_topic: Командный MQTT-топик для отправки команды (String, обязательно).
* OnOff_state_topic: MQTT-топик обратной связи для получения состояния (String, обязательно).
* payload_on: Сообщение для включения (String, обязательно).
* payload_off: Сообщение для выключения (String, обязательно).

Пример::

    {
        "block": 1,
        "type": "light",
        "data": 
        {
            "param_1": "Фонари",
            "param_2": "Двор",
            "setting_name": "Фонари",
            "icon": "\uDB84\uDC20",
            "variant_type": "Light_variant_OnOff",
            "variant": 
            {
            "OnOff_command_topic": "panel/light/1/OnOff_command",
            "OnOff_state_topic": "panel/light/1/OnOff_state",
            "payload_on": "1",
            "payload_off": "0"
            }
        }
    }

.. image:: /images/1.png

\* Пример введенного блока


Подтип light_variant_dimmer
---------------------------

Отправляет указанную команду включения/выключения на командный MQTT-топик, а также прослушивает MQTT-топик обратной связи для измения состояния элементов интерфейса. В дополнении к этому отправляет значение яркости на командный MQTT-топик значение яркости, прослушивает MQTT-топик обратной связи для измения состояния элементов интерфейса. Параметры ``variant``:

.. image:: /images/Screenshot_20250526_192314.png

\* **Блок 1** - Состояние выкл, **Блок 2** - Состояние вкл, яркость 0%, **Блок 3** - Состояние вкл, яркость 46%, **Блок 4** - Состояние вкл, яркость 100%.

* OnOff_command_topic: Командный MQTT-топик для отправки команды (String, обязательно).
* OnOff_state_topic: MQTT-топик обратной связи для получения состояния (String, обязательно).
* payload_on: Сообщение для включения (String, обязательно).
* payload_off: Сообщение для выключения (String, обязательно).
* brightness_command_topic: Топик для отправки яркости (String, обязательно).
* brightness_state_topic: Топик для получения яркости (String, обязательно).
* brightness_scale: Максимальное значение яркости (Int, обязательно).

Пример::

    {
        "block": 1,
        "type": "light",
        "data": {
            "param_1": "Торшеры",
            "param_2": "Спальня",
            "setting_name": "Торшеры",
            "icon": "\uDB85\uDFD1",
            "variant_type": "Light_variant_dimmer",
            "variant": 
            {
                "OnOff_command_topic": "panel/light/2/OnOff_command",
                "OnOff_state_topic": "panel/light/2/OnOff_state",
                "payload_on": "1",
                "payload_off": "0",
                "brightness_command_topic": "panel/light/2/brightness_command",
                "brightness_state_topic": "panel/light/2/brightness_state",
                "brightness_scale": 100
            }
        }
    }

.. container:: image-row

    .. figure:: /images/Screenshot_20250526_192849.png
        :width:200px

        \* Пример введенного блока

    .. figure:: /images/setting_dimmer_bright.png
        :width:200px

        \* Страница настроек

Подтип light_variant_color
---------------------------
Отправляет указанную команду включения/выключения на командный MQTT-топик, а также прослушивает MQTT-топик обратной связи для измения состояния элементов интерфейса. В дополнении к этому отправляет значение яркости на командный MQTT-топик значение яркости, прослушивает MQTT-топик обратной связи для измения состояния элементов интерфейса. Помимо этого, отправляет выбранный цвет на командный MQTT-топик (RGB). Параметры ``variant``:

* OnOff_command_topic: Командный MQTT-топик для отправки команды (String, обязательно).
* OnOff_state_topic: MQTT-топик обратной связи для получения состояния (String, обязательно).
* payload_on: Сообщение для включения (String, обязательно).
* payload_off: Сообщение для выключения (String, обязательно).
* brightness_command_topic: Топик для отправки яркости (String, обязательно).
* brightness_state_topic: Топик для получения яркости (String, обязательно).
* brightness_scale: Максимальное значение яркости (Int, обязательно).
* color_command_topic: Топик для отправки цвета (String, обязательно).

Пример::

    {
        "block": 1,
        "type": "light",
        "data": {
            "param_1": "Подсветка",
            "param_2": "Раб. место",
            "setting_name": "Раб. место",
            "icon": "\uDB84\uDC51",
            "variant_type": "Light_variant_color",
            "variant": 
            {
                "OnOff_command_topic": "panel/light/3/OnOff_command",
                "OnOff_state_topic": "panel/light/3/OnOff_state",
                "payload_on": "1",
                "payload_off": "0",
                "brightness_command_topic": "panel/light/3/brightness_command",
                "brightness_state_topic": "panel/light/3/brightness_state",
                "brightness_scale": 100,
                "color_command_topic": "panel/light/3/color_command"
            }
        }
    }

.. image:: /images/block_rgb.png

.. image:: /images/setting_rgb_1.png
    
.. image:: /images/setting_rgb_2.png
    
.. image:: /images/setting_rgb_3.png

Подтип light_variant_temperature
-----------------------------------

Добавляет регулировку цветовой температуры. Параметры ``variant``:

* OnOff_command_topic: Командный MQTT-топик для отправки команды (String, обязательно).
* OnOff_state_topic: MQTT-топик обратной связи для получения состояния (String, обязательно).
* payload_on: Сообщение для включения (String, обязательно).
* payload_off: Сообщение для выключения (String, обязательно).
* brightness_command_topic: Топик для отправки яркости (String, обязательно).
* brightness_state_topic: Топик для получения яркости (String, обязательно).
* brightness_scale: Максимальное значение яркости (Int, обязательно).
* temp_command_topic: Топик для отправки температуры (String, обязательно).
* temp_state_topic: Топик для получения температуры (String, обязательно).
* max_temp: Максимальная температура (Int, обязательно).
* min_temp: Минимальная температура (Int, обязательно).


Пример::

    {
        "block": 1,
        "type": "light",
        "data": {
            "param_1": "",
            "param_2": "Свесы",
            "setting_name": "Свесы",
            "icon": "\uDB86\uDCDE",
            "variant_type": "Light_variant_temperature",
            "variant": 
            {
                "OnOff_command_topic": "panel/light/4/OnOff_command",
                "OnOff_state_topic": "panel/light/4/OnOff_state",
                "payload_on": "1",
                "payload_off": "0",
                "brightness_command_topic": "panel/light/4/brightness_command",
                "brightness_state_topic": "panel/light/4/brightness_state",
                "brightness_scale": 100,
                "temp_command_topic": "panel/light/4/temp_command",
                "temp_state_topic": "panel/light/4/temp_state",
                "max_temp": 6500,
                "min_temp": 2700
            }
        }
    }


.. image:: /images/block_dimmer_temp.png

.. image:: /images/setting_dimmer_temp.png
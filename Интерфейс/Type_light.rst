Тип light (Свет)
=================

Блок ``light`` предназначен для управления освещением и поддерживает четыре типа устройства. При кратковременном нажатии на блок отправляется команда включения или выключения (``payload_on`` / ``payload_off``). При длительном удержании открывается страница настроек блока (за исключением типа ``light_variant_OnOff``). Общие параметры:

* :ref:`light-param_1` — назначение блока (например, тип устройства: «Люстра», «Подсветка»).
* :ref:`light-param_2` — локация или контекст использования (например, «Кухня», «Гостиная»).
* :ref:`light-setting_name` — название устройства в настройках.
* :ref:`light-icon` — иконка, отображаемая на блоке.
* :ref:`light-variant` — объект с параметрами выбранного варианта устройства.
* :ref:`light-variant_type` — тип устройства (вариант функциональности):
   * :ref:`light_variant_OnOff` — устройство с включением/выключением.
   * :ref:`light_variant_dimmer` — устройство с регулировкой яркости.
   * :ref:`light_variant_temperature` — устройство с регулировкой яркости и температуры цвета.
   * :ref:`light_variant_color` — устройство с регулировкой яркости и цвета (RGB).

.. raw:: html

    <br/><br/>
    <br/><br/>

Детальный разбор параметров:
----------------------------

.. _light-param_1:
param_1
*******
   Используется для изменения текста в UI-блоке, например, чтобы указать, что это «Люстра» или «Торшеры». Может применяться и в других целях.

   :имя поля: ``param_1``
   :тип объекта: ``String``
   :наличие значения: Может быть пустым
   :ограничение строки: 9 символов
   :пример-1: ``"param_1":"Торшеры"``
   :пример-2: ``"param_1":"Освещение"``
   :пример-3: ``"param_1":""``

.. image:: /images/light-param_1.png
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
   :пример-1: ``"param_2":"Спальня"``
   :пример-2: ``"param_2":"Прихожая"``
   :пример-3: ``"param_2":"Торшеры"``

.. image:: /images/light-param_2.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _light-setting_name:
setting_name
************
   Используется для изменения текста в UI-настройках. Обычно можно продублировать значение из ``param_2``, но иногда бывают ситуации когда в блоке пришлось написать сокращенно, то в настройках можно написать полностью.

   :имя поля: ``setting_name``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: 14 символов
   :пример-1: ``"setting_name":"Торшеры"``
   :пример-2: ``"setting_name":"Точки"``
   :пример-3: ``"setting_name":"Подсветка"``

.. image:: /images/light-setting_name.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _light-icon:
icon
****
   Используется для изменения иконки в UI-блоке.

   :имя поля: ``icon``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Стандартный unicode
   :пример-1: ``"icon":"\uDB81\uDF64"`` - иконка 
   :пример-2: ``"icon":"\uDB86\uDCDE"`` - иконка
   :пример-3: ``"icon":"\uDB84\uDC51"`` - иконка

.. image:: /images/light-icon.png
.. raw:: html

    <br/><br/>
    <br/><br/>

.. _light-variant_type:
variant_type
************
   Используется для указания названия под-варианта(под-типа) устройства-освещения.

   * имя поля: ``variant_type``
   * тип объекта: ``String``
   * наличие значения: Обязательно
   * ограничение строки: Только заданные значения
   * **варианты:**
      * :ref:`light-light_variant_OnOff` — устройство с включением/выключением.
      * :ref:`light-light_variant_dimmer` — устройство с включением/выключением и регулировкой яркости.
      * :ref:`light-light_variant_temperature` — устройство с включением/выключением, регулировкой яркости и температуры цвета.
      * :ref:`light-light_variant_color` — устройство с включением/выключением, регулировкой яркости и цвета (RGB).


.. raw:: html

    <br/><br/>


.. _light-variant:
variant
*******
   Поле ``variant`` содержит параметры, соответствующие выбранному типу устройства (``variant_type``). Ниже приведены описания параметров для каждого из подтипов.

.. raw:: html

    <br/><br/>
    <br/><br/>
    <br/><br/>

.. _light_variant_OnOff:
light_variant_OnOff
--------------------------

Отправляет указанную команду включения или выключения (``payload_on`` / ``payload_off``) на командный MQTT-топик ``OnOff_command_topic``, а также отслеживает состояние устройства через MQTT-топик обратной свзяи ``OnOff_state_topic`` для обновления элементов интерфейса.

.. image:: /images/OnOffBlocks.png

\* **Блок 1** - Состояние выкл, **Блок 2** - Состояние вкл.

Параметры ``variant``:

OnOff_command_topic
*******
   Командный MQTT-топик, куда отправляется команда.

   :имя поля: ``OnOff_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"OnOff_command_topic":"поменять"``
   :пример-2: ``"OnOff_command_topic":"поменять"``
   :пример-3: ``"OnOff_command_topic":"поменять"``

OnOff_state_topic
*******
   MQTT-топик обратной связи, куда должный приходить сообщения включения и выключения.

   :имя поля: ``OnOff_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"OnOff_state_topic":"поменять"``
   :пример-2: ``"OnOff_state_topic":"поменять"``
   :пример-3: ``"OnOff_state_topic":"поменять"``

payload_on
*******
   Командна включения, которая отправляется на командный MQTT-топик(``OnOff_command_topic``) и если приходит такая команда на MQTT-топик обратной связи(``OnOff_state_topic``), обновляет элементы интерфейса на включено.

   :имя поля: ``payload_on``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_on":"поменять"``
   :пример-2: ``"payload_on":"поменять"``
   :пример-3: ``"payload_on":"поменять"``

payload_off
*******
   Командна выключения, которая отправляется на командный MQTT-топик(``OnOff_command_topic``) и если приходит такая команда на MQTT-топик обратной связи(``OnOff_state_topic``), обновляет элементы интерфейса на выключено.

   :имя поля: ``payload_off``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_off":"поменять"``
   :пример-2: ``"payload_off":"поменять"``
   :пример-3: ``"payload_off":"поменять"``

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

..  _light_variant_dimmer:
light_variant_dimmer
---------------------------

Отправляет указанную команду включения или выключения (``payload_on`` / ``payload_off``) на командный MQTT-топик ``OnOff_command_topic``, а также отслеживает состояние устройства через MQTT-топик обратной свзяи ``OnOff_state_topic`` для обновления элементов интерфейса. В дополнении к этому отправляет значение яркости (``brightness_scale``) на командный MQTT-топик ``brightness_command_topic`` значение яркости, прослушивает MQTT-топик обратной связи ``brightness_state_topic`` для измения состояния элементов интерфейса. Параметры ``variant``:

.. image:: /images/lights/brightness_block_and_page.png

Параметры ``variant``:

OnOff_command_topic
*******
   Командный MQTT-топик, куда отправляется команда.

   :имя поля: ``OnOff_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"OnOff_command_topic":"поменять"``
   :пример-2: ``"OnOff_command_topic":"поменять"``
   :пример-3: ``"OnOff_command_topic":"поменять"``

OnOff_state_topic
*******
   MQTT-топик обратной связи, куда должны приходить сообщения включения и выключения.

   :имя поля: ``OnOff_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"OnOff_state_topic":"поменять"``
   :пример-2: ``"OnOff_state_topic":"поменять"``
   :пример-3: ``"OnOff_state_topic":"поменять"``

payload_on
*******
   Командна включения, которая отправляется на командный MQTT-топик (``OnOff_command_topic``) и если приходит такая команда на MQTT-топик обратной связи(``OnOff_state_topic``), обновляет элементы интерфейса на включено.

   :имя поля: ``payload_on``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_on":"поменять"``
   :пример-2: ``"payload_on":"поменять"``
   :пример-3: ``"payload_on":"поменять"``

payload_off
*******
   Командна выключения, которая отправляется на командный MQTT-топик (``OnOff_command_topic``) и если приходит такая команда на MQTT-топик обратной связи(``OnOff_state_topic``), обновляет элементы интерфейса на выключено.

   :имя поля: ``payload_off``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_off":"поменять"``
   :пример-2: ``"payload_off":"поменять"``
   :пример-3: ``"payload_off":"поменять"``

brightness_command_topic
*******
   Командный MQTT-топик, куда отправляется значение яркости.

   :имя поля: ``brightness_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"brightness_command_topic":"поменять"``
   :пример-2: ``"brightness_command_topic":"поменять"``
   :пример-3: ``"brightness_command_topic":"поменять"``

brightness_state_topic
*******
   MQTT-топик обратной связи, куда должны приходить сообщения со значением яркости.

   :имя поля: ``brightness_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"brightness_state_topic":"поменять"``
   :пример-2: ``"brightness_state_topic":"поменять"``
   :пример-3: ``"brightness_state_topic":"поменять"``


brightness_scale
*******
   Максимальное значение яркости.

   :имя поля: ``brightness_scale``
   :тип объекта: ``Int``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"brightness_scale":"поменять"``
   :пример-2: ``"brightness_scale":"поменять"``
   :пример-3: ``"brightness_scale":"поменять"``
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
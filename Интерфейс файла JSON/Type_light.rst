Тип light (Свет)
================

.. image:: /images/light/blocks.png

Блок ``light`` предназначен для управления освещением и поддерживает четыре типа устройств. При кратковременном нажатии на блок отправляется команда включения или выключения (``payload_on`` / ``payload_off``). При длительном удержании открывается страница настроек блока (за исключением типа ``light_variant_OnOff``). Общие параметры:

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


Полный пример всего освещения:
    * :ref:`light-full_settings`

.. raw:: html

    <br/><br/>
    <br/><br/>

Детальный разбор параметров:
----------------------------

.. _light-param_1:
param_1
*******
   Используется для изменения текста в самом блоке, например, чтобы указать, что это «Люстра» или «Торшеры». Может применяться и в других целях.

   :имя поля: ``param_1``
   :тип объекта: ``String``
   :наличие значения: Может быть пустым
   :ограничение строки: 9 символов
   :пример-1: ``"param_1":"Торшеры"``
   :пример-2: ``"param_1":"Освещение"``
   :пример-3: ``"param_1":""``

.. image:: /images/light/param_1.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _light-param_2:
param_2
*******
   Используется для изменения текста в самом блоке. Например, позволяет уточнить, где будет находиться данное устройство-освещение. Если панель установлена в конкретной комнате, а все освещение относится к ней, это поле можно оставить пустым и написать значение из ``param_1`` сюда.

   :имя поля: ``param_2``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: 11 символов
   :пример-1: ``"param_2":"Спальня"``
   :пример-2: ``"param_2":"Прихожая"``
   :пример-3: ``"param_2":"Торшеры"``

.. image:: /images/light/param_2.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _light-setting_name:
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

.. image:: /images/light/setting_name.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _light-icon:
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

.. image:: /images/light/icon.png
.. raw:: html

    <br/><br/>
    <br/><br/>

.. _light-variant_type:
variant_type
************
   Используется для указания названия подтипа устройства-освещения.

   * имя поля: ``variant_type``
   * тип объекта: ``String``
   * наличие значения: Обязательно
   * ограничение строки: Только заданные значения
   * **варианты:**
      * :ref:`light_variant_OnOff` — устройство с включением/выключением.
      * :ref:`light_variant_dimmer` — устройство с включением/выключением и регулировкой яркости.
      * :ref:`light_variant_temperature` — устройство с включением/выключением, регулировкой яркости и температуры цвета.
      * :ref:`light_variant_color` — устройство с включением/выключением, регулировкой яркости и цвета (RGB).


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
-------------------

Отправляет команду включения или выключения (``payload_on`` / ``payload_off``) на командный MQTT-топик ``OnOff_command_topic``, а также отслеживает состояние устройства через MQTT-топик обратной связи ``OnOff_state_topic`` для обновления элементов интерфейса.

.. image:: /images/light/light_variant_OnOff.png

Параметры ``variant``:

* :ref:`light_variant_OnOff-OnOff_command_topic`: Командный MQTT-топик для отправки команды (String, обязательно).
* :ref:`light_variant_OnOff-OnOff_state_topic`: MQTT-топик обратной связи для получения состояния (String, обязательно).
* :ref:`light_variant_OnOff-payload_on`: Команда(Сообщение) для включения (String, обязательно).
* :ref:`light_variant_OnOff-payload_off`: Команда(Сообщение) для выключения (String, обязательно).

.. _light_variant_OnOff-OnOff_command_topic:
OnOff_command_topic
*******************
   Командный MQTT-топик, куда отправляется команда.

   :имя поля: ``OnOff_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"OnOff_command_topic":"panel/light/1/OnOff_command"``

.. _light_variant_OnOff-OnOff_state_topic:
OnOff_state_topic
*****************
   MQTT-топик обратной связи, куда приходят сообщения включения и выключения.

   :имя поля: ``OnOff_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"OnOff_state_topic":"panel/light/1/OnOff_state"``

.. _light_variant_OnOff-payload_on:
payload_on
**********
   Команда включения, которая отправляется на командный MQTT-топик(``OnOff_command_topic``) и если такая команда приходит на MQTT-топик обратной связи (``OnOff_state_topic``), интерфейс обновляется на состояние «включено».

   :имя поля: ``payload_on``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_on":"1"``
   :пример-2: ``"payload_on":"ON"``
   :пример-3: ``"payload_on":"true"``

.. _light_variant_OnOff-payload_off:
payload_off
***********
   Команда выключения, которая отправляется на командный MQTT-топик(``OnOff_command_topic``) и если такая команда приходит на MQTT-топик обратной связи (``OnOff_state_topic``), интерфейс обновляется на состояние «выключено».

   :имя поля: ``payload_off``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_off":"0"``
   :пример-2: ``"payload_off":"OFF"``
   :пример-3: ``"payload_off":"false"``

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
         "variant_type": "light_variant_OnOff",
         "variant": 
         {
            "OnOff_command_topic": "panel/light/1/OnOff_command",
            "OnOff_state_topic": "panel/light/1/OnOff_state",
            "payload_on": "1",
            "payload_off": "0"
         }
      }
   }

.. raw:: html

    <br/><br/>
    <br/><br/>

..  _light_variant_dimmer:
light_variant_dimmer
--------------------

Отправляет указанную команду включения или выключения (``payload_on`` / ``payload_off``) на командный MQTT-топик ``OnOff_command_topic``, а также отслеживает состояние устройства через MQTT-топик обратной связи ``OnOff_state_topic`` для обновления элементов интерфейса. В дополнении к этому отправляет значение яркости (``brightness_scale``) на командный MQTT-топик ``brightness_command_topic`` значение яркости, прослушивает MQTT-топик обратной связи ``brightness_state_topic`` для изменения состояния элементов интерфейса.

.. image:: /images/light/light_variant_dimmer.png

Параметры ``variant``:

* :ref:`light_variant_dimmer-OnOff_command_topic`: Командный MQTT-топик для отправки команды.
* :ref:`light_variant_dimmer-OnOff_state_topic`: MQTT-топик обратной связи для получения состояния.
* :ref:`light_variant_dimmer-payload_on`: Команда (Сообщение) для включения.
* :ref:`light_variant_dimmer-payload_off`: Команда (Сообщение) для выключения.
* :ref:`light_variant_dimmer-brightness_command_topic`: Командный MQTT-топик для отправки яркости.
* :ref:`light_variant_dimmer-brightness_state_topic`: MQTT-топик обратной связи для получения яркости.
* :ref:`light_variant_dimmer-brightness_scale`: Максимальное значение яркости.

.. _light_variant_dimmer-OnOff_command_topic:
OnOff_command_topic
*******************
   Командный MQTT-топик, куда отправляется команда.

   :имя поля: ``OnOff_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"OnOff_command_topic":"panel/light/2/OnOff_command"``

.. _light_variant_dimmer-OnOff_state_topic:
OnOff_state_topic
*****************
   MQTT-топик обратной связи, откуда приходят сообщения состояния (включения и выключения).

   :имя поля: ``OnOff_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"OnOff_state_topic":"panel/light/2/OnOff_state"``

.. _light_variant_dimmer-payload_on:
payload_on
**********
   Команда включения, которая отправляется на командный MQTT-топик (``OnOff_command_topic``) и если такая команда приходит на MQTT-топик обратной связи (``OnOff_state_topic``), интерфейс обновляется на состояние «включено».

   :имя поля: ``payload_on``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_on":"1"``
   :пример-2: ``"payload_on":"ON"``
   :пример-3: ``"payload_on":"true"``

.. _light_variant_dimmer-payload_off:
payload_off
***********
   Команда выключения, которая отправляется на командный MQTT-топик (``OnOff_command_topic``) и если такая команда приходит на MQTT-топик обратной связи (``OnOff_state_topic``), интерфейс обновляется на состояние «выключено».

   :имя поля: ``payload_off``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_off":"0"``
   :пример-2: ``"payload_off":"OFF"``
   :пример-3: ``"payload_off":"false"``

.. _light_variant_dimmer-brightness_command_topic:
brightness_command_topic
************************
   Командный MQTT-топик, куда отправляется значение яркости.

   :имя поля: ``brightness_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"brightness_command_topic":"panel/light/2/brightness_command"``

.. _light_variant_dimmer-brightness_state_topic:
brightness_state_topic
**********************
   MQTT-топик обратной связи, куда приходят сообщения со значением яркости.

   :имя поля: ``brightness_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"brightness_state_topic":"panel/light/2/brightness_state"``

.. _light_variant_dimmer-brightness_scale:
brightness_scale
****************
   Максимальное значение яркости.

   :имя поля: ``brightness_scale``
   :тип объекта: ``Integer``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"brightness_scale":"100"``
   :пример-2: ``"brightness_scale":"255"``
   :пример-3: ``"brightness_scale":"1023"``


Пример::

   {
      "block": 1,
      "type": "light",
      "data": {
         "param_1": "Торшеры",
         "param_2": "Спальня",
         "setting_name": "Торшеры",
         "icon": "\uDB85\uDFD1",
         "variant_type": "light_variant_dimmer",
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

.. raw:: html

    <br/><br/>
    <br/><br/>

.. _light_variant_color:
light_variant_color
-------------------
Отправляет указанную команду включения/выключения на командный MQTT-топик, а также прослушивает MQTT-топик обратной связи для изменения состояния элементов интерфейса. В дополнении к этому отправляет значение яркости на командный MQTT-топик значение яркости, прослушивает MQTT-топик обратной связи для изменения состояния элементов интерфейса. Помимо этого, отправляет выбранный цвет на командный MQTT-топик (RGB).

.. image:: /images/light/light_variant_color.png

Параметры ``variant``:

* :ref:`light_variant_color-OnOff_command_topic`: Командный MQTT-топик для отправки команды (String, обязательно).
* :ref:`light_variant_color-OnOff_state_topic`: MQTT-топик обратной связи для получения состояния (String, обязательно).
* :ref:`light_variant_color-payload_on`: Команда(Сообщение) для включения (String, обязательно).
* :ref:`light_variant_color-payload_off`: Команда(Сообщение) для выключения (String, обязательно).
* :ref:`light_variant_color-brightness_command_topic`: Командный MQTT-топик для отправки яркости (String, обязательно).
* :ref:`light_variant_color-brightness_state_topic`: MQTT-топик обратной связи для получения яркости (String, обязательно).
* :ref:`light_variant_color-brightness_scale`: Максимальное значение яркости (Integer, обязательно).
* :ref:`light_variant_color-color_command_topic`: Командный MQTT-топик для отправки цвета (String, обязательно).

.. _light_variant_color-OnOff_command_topic:
OnOff_command_topic
*******************
   Командный MQTT-топик, куда отправляется команда.

   :имя поля: ``OnOff_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"OnOff_command_topic":"panel/light/3/OnOff_command"``

.. _light_variant_color-OnOff_state_topic:
OnOff_state_topic
*****************
   MQTT-топик обратной связи, куда приходят сообщения включения и выключения.

   :имя поля: ``OnOff_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"OnOff_state_topic":"panel/light/3/OnOff_state"``

.. _light_variant_color-payload_on:
payload_on
**********
   Команда включения, которая отправляется на командный MQTT-топик(``OnOff_command_topic``) и если такая команда приходит на MQTT-топик обратной связи (``OnOff_state_topic``), интерфейс обновляется на состояние «включено».

   :имя поля: ``payload_on``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_on":"1"``
   :пример-2: ``"payload_on":"ON"``
   :пример-3: ``"payload_on":"true"``

.. _light_variant_color-payload_off:
payload_off
***********
   Команда выключения, которая отправляется на командный MQTT-топик(``OnOff_command_topic``) и если такая команда приходит на MQTT-топик обратной связи (``OnOff_state_topic``), интерфейс обновляется на состояние «выключено».

   :имя поля: ``payload_off``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_off":"0"``
   :пример-2: ``"payload_off":"OFF"``
   :пример-3: ``"payload_off":"false"``

.. _light_variant_color-brightness_command_topic:
brightness_command_topic
************************
   Командный MQTT-топик, куда отправляется значение яркости.

   :имя поля: ``brightness_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"brightness_command_topic":"panel/light/3/brightness_command"``

.. _light_variant_color-brightness_state_topic:
brightness_state_topic
**********************
   MQTT-топик обратной связи, куда приходят сообщения со значением яркости.

   :имя поля: ``brightness_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"brightness_state_topic":"panel/light/3/brightness_state"``

.. _light_variant_color-brightness_scale:
brightness_scale
****************
   Максимальное значение яркости.

   :имя поля: ``brightness_scale``
   :тип объекта: ``Integer``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"brightness_scale":100``
   :пример-2: ``"brightness_scale":255``
   :пример-3: ``"brightness_scale":1023``

.. _light_variant_color-color_command_topic:
color_command_topic
*******************
   Командный MQTT-топик, куда отправляется значение выбранного цвета в формате RGB. Пример сообщения ``255;0;0`` - красный цвет.

   :имя поля: ``color_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"color_command_topic":"panel/light/3/color_command"``


Пример::

   {
      "block": 1,
      "type": "light",
      "data": {
         "param_1": "Подсветка",
         "param_2": "Раб. место",
         "setting_name": "Рабочее место",
         "icon": "\uDB84\uDC51",
         "variant_type": "light_variant_color",
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

.. raw:: html

    <br/><br/>
    <br/><br/>

.. _light_variant_temperature:
light_variant_temperature
-------------------------

Добавляет регулировку цветовой температуры.

.. image:: /images/light/light_variant_temperature.png

Параметры ``variant``:

* :ref:`light_variant_temperature-OnOff_command_topic`: Командный MQTT-топик для отправки команды (String, обязательно).
* :ref:`light_variant_temperature-OnOff_state_topic`: MQTT-топик обратной связи для получения состояния (String, обязательно).
* :ref:`light_variant_temperature-payload_on`: Команда(Сообщение) для включения (String, обязательно).
* :ref:`light_variant_temperature-payload_off`: Команда(Сообщение) для выключения (String, обязательно).
* :ref:`light_variant_temperature-brightness_command_topic`: Командный MQTT-топик для отправки яркости (String, обязательно).
* :ref:`light_variant_temperature-brightness_state_topic`: MQTT-топик обратной связи для получения яркости (String, обязательно).
* :ref:`light_variant_temperature-brightness_scale`: Максимальное значение яркости (Integer, обязательно).
* :ref:`light_variant_temperature-temp_command_topic`: Командный MQTT-топик для отправки температуры (String, обязательно).
* :ref:`light_variant_temperature-temp_state_topic`: MQTT-топик обратной связи для получения температуры (String, обязательно).
* :ref:`light_variant_temperature-max_temp`: Максимальная температура (Integer, обязательно).
* :ref:`light_variant_temperature-min_temp`: Минимальная температура (Integer, обязательно).

.. _light_variant_temperature-OnOff_command_topic:
OnOff_command_topic
*******************
   Командный MQTT-топик, куда отправляется команда.

   :имя поля: ``OnOff_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"OnOff_command_topic":"panel/light/4/OnOff_command"``

.. _light_variant_temperature-OnOff_state_topic:
OnOff_state_topic
*****************
   MQTT-топик обратной связи, куда приходят сообщения включения и выключения.

   :имя поля: ``OnOff_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"OnOff_state_topic":"panel/light/4/OnOff_state"``

.. _light_variant_temperature-payload_on:
payload_on
**********
   Команда включения, которая отправляется на командный MQTT-топик(``OnOff_command_topic``) и если такая команда приходит на MQTT-топик обратной связи (``OnOff_state_topic``), интерфейс обновляется на состояние «включено».

   :имя поля: ``payload_on``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_on":"1"``
   :пример-2: ``"payload_on":"ON"``
   :пример-3: ``"payload_on":"true"``

.. _light_variant_temperature-payload_off:
payload_off
***********
   Команда выключения, которая отправляется на командный MQTT-топик(``OnOff_command_topic``) и если такая команда приходит на MQTT-топик обратной связи (``OnOff_state_topic``), интерфейс обновляется на состояние «выключено».

   :имя поля: ``payload_off``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"payload_off":"0"``
   :пример-2: ``"payload_off":"OFF"``
   :пример-3: ``"payload_off":"false"``

.. _light_variant_temperature-brightness_command_topic:
brightness_command_topic
************************
   Командный MQTT-топик, куда отправляется значение яркости.

   :имя поля: ``brightness_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"brightness_command_topic":"panel/light/4/brightness_command"``

.. _light_variant_temperature-brightness_state_topic:
brightness_state_topic
**********************
   MQTT-топик обратной связи, куда приходят сообщения со значением яркости.

   :имя поля: ``brightness_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"brightness_state_topic":"panel/light/4/brightness_state"``

.. _light_variant_temperature-brightness_scale:
brightness_scale
****************
   Максимальное значение яркости.

   :имя поля: ``brightness_scale``
   :тип объекта: ``Integer``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример-1: ``"brightness_scale":100``
   :пример-2: ``"brightness_scale":255``
   :пример-3: ``"brightness_scale":1023``

.. _light_variant_temperature-temp_command_topic:
temp_command_topic
******************
   Командный MQTT-топик, куда отправляется значение температуры света.

   :имя поля: ``temp_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"temp_command_topic":"panel/light/4/temp_command"``

.. _light_variant_temperature-temp_state_topic:
temp_state_topic
****************
   MQTT-топик обратной связи, куда приходят сообщения со значением температуры света.

   :имя поля: ``temp_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"temp_state_topic":"panel/light/4/temp_state"``

.. _light_variant_temperature-max_temp:
max_temp
********
   Максимальное значение температуры света.

   :имя поля: ``max_temp``
   :тип объекта: ``Integer``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"max_temp":6500``

.. _light_variant_temperature-min_temp:
min_temp
********
   Минимальное значение температуры света.

   :имя поля: ``min_temp``
   :тип объекта: ``Integer``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"min_temp":2700``

Пример::

   {
      "block": 1,
      "type": "light",
      "data": {
         "param_1": "",
         "param_2": "Свесы",
         "setting_name": "Свесы",
         "icon": "\uDB86\uDCDE",
         "variant_type": "light_variant_temperature",
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

.. raw:: html

    <br/><br/>
    <br/><br/>


.. _light-full_settings:
Общий пример страницы всего света
---------------------------------

Пример из всех типов::

   {
      "screens": [
         {
            "page": 1,
            "blocks": [
               {
                  "block": 1,
                  "type": "light",
                  "data": {
                     "param_1": "Фонари",
                     "param_2": "Двор",
                     "setting_name": "Фонари",
                     "icon": "\uDB84\uDC20",
                     "variant_type": "light_variant_OnOff",
                     "variant": {
                        "OnOff_command_topic": "panel/light/1/OnOff_command",
                        "OnOff_state_topic": "panel/light/1/OnOff_state",
                        "payload_on": "1",
                        "payload_off": "0"
                     }
                  }
               },
               {
                  "block": 2,
                  "type": "light",
                  "data": {
                     "param_1": "Торшеры",
                     "param_2": "Спальня",
                     "setting_name": "Торшеры",
                     "icon": "\uDB85\uDFD1",
                     "variant_type": "light_variant_dimmer",
                     "variant": {
                        "OnOff_command_topic": "panel/light/2/OnOff_command",
                        "OnOff_state_topic": "panel/light/2/OnOff_state",
                        "payload_on": "1",
                        "payload_off": "0",
                        "brightness_command_topic": "panel/light/2/brightness_command",
                        "brightness_state_topic": "panel/light/2/brightness_state",
                        "brightness_scale": 255
                     }
                  }
               },
               {
                  "block": 3,
                  "type": "light",
                  "data": {
                     "param_1": "Подсветка",
                     "param_2": "Раб. место",
                     "setting_name": "Подсветка",
                     "icon": "\uDB84\uDC51",
                     "variant_type": "light_variant_color",
                     "variant": {
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
               },
               {
                  "block": 4,
                  "type": "light",
                  "data": {
                     "param_1": "",
                     "param_2": "Свесы",
                     "setting_name": "Свесы",
                     "icon": "\uDB86\uDCDE",
                     "variant_type": "light_variant_temperature",
                     "variant": {
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
            ]
         }
      ]
   }
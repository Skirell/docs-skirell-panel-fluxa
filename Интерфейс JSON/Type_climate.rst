Тип climate (Климат)
====================

.. image:: /images/climate/main.png

Блок ``climate`` используется для управления различными климатическими устройствами. Поддерживает два типа устройств: базовый термостат и расширенный кондиционер. При кратковременном нажатии на блок открывается страница его настроек. Общие параметры:

* :ref:`climate-param_1` — назначение блока (например, тип устройства: «Тёплый пол», «Увлажнитель»).
* :ref:`climate-param_2` — локация или контекст использования (например, «Кухня», «Гостиная»).
* :ref:`climate-setting_name` — название устройства в настройках.
* :ref:`climate-icon` — иконка, отображаемая на блоке.
* :ref:`climate-min_target` - минимальное значение целевой (заданной) температуры.
* :ref:`climate-max_target` - максимальное значение целевой (заданной) температуры.
* :ref:`climate-measure` - единица измерения (например: «°C»).
* :ref:`climate-color` - цвет индикатора термостата в активном состоянии (кроме режима «Выключено»).
* :ref:`climate-variant` — объект с параметрами выбранного варианта устройства.
* :ref:`climate-variant_type` — тип устройства (вариант функциональности):
   * :ref:`climate_variant_cond` — расширенный термостат с поддержкой от 2 до 5 режимов работы и от 0 до 5 режимов вентиляции.
   * :ref:`climate_variant_thermostat` — базовый термостат с режимами «Включено»/«Выключено», с возможностью подключения до трёх датчиков.

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
   Используется для изменения текстового поля в самом блоке, например, чтобы указать, что это «Тёплый пол» или «Увлажнитель». Может применяться и в других целях.

   :имя поля: ``param_1``
   :тип объекта: ``String``
   :наличие значения: Может быть пустым
   :ограничение строки: 9 символов
   :пример-1: ``"param_1":"Конд-ер"``
   :пример-2: ``"param_1":"Тепл. пол"``
   :пример-3: ``"param_1":""``

.. image:: /images/climate/param_1.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _climate-param_2:
param_2
*******
   Используется для изменения текстового поля в самом блоке. Например, позволяет уточнить, где будет находиться данное климатическое устройство. Если панель установлена в конкретной комнате, а все климатические устройства относятся к ней, это поле можно оставить пустым и написать значение из ``param_1`` сюда.

   :имя поля: ``param_2``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: 11 символов
   :пример-1: ``"param_2":"Кондиционер"``
   :пример-2: ``"param_2":"Детская"``
   :пример-3: ``"param_2":""``

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
   :пример-1: ``"setting_name":"Вентиляция"``
   :пример-2: ``"setting_name":"Кондиционер"``
   :пример-3: ``"setting_name":"Теплый пол"``

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
   Устанавливает минимальное допустимое значение параметра (уставки, целевого значения), которое можно выбрать с помощью кругового слайдера. Пользователь не сможет установить значение меньше этого порога.

   :имя поля: ``min_target``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"min_target":"15"``


.. _climate-max_target:
max_target
****
   Устанавливает максимальное допустимое значение параметра (уставки, целевого значения), которое можно выбрать с помощью кругового слайдера. Пользователь не сможет установить значение больше этого порога.

   :имя поля: ``max_target``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"max_target":"30"``


.. _climate-measure:
measure
*******
   Устанавливает единицу измерения параметра (уставки, целевого значения), например, чтобы указать, что это единица измерения «°C» или «%». Может применяться и в других целях.

   :имя поля: ``measure``
   :тип объекта: ``String``
   :наличие значения: Может быть пустым
   :ограничение строки: 5 символов
   :пример-1: ``"measure":"°C"``
   :пример-2: ``"measure":"%"``

.. image:: /images/climate/measure.png
.. raw:: html

    <br/><br/>
    <br/><br/>


.. _climate-color:
color
*******
   Используется как цвет для активного состояния устройства (при режиме ВКЛ). Имеет ряд особенностей:
      * В подтипе ``climate_variant_thermostat`` данный параметр отвечает за цвет блока в интерфейсе, а также за цвет кругового слайдера (чем пользователь задает значение-уставку) внутри страницы настроек.
      * В подтипе ``climate_variant_cond`` данный параметр отвечает только за цвет блока в интерфейсе. Цвета кругового слайдера внутри страницы настроек задаются другими параметрами, внутри подтипа устройств.
    Также важно учесть, что названия цветов указываются строго из таблицы, представленной ниже.
   
   :имя поля: ``color``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Только заданные значения
   :пример-1: ``"color":"color_red"``
   :пример-2: ``"color":"color_green"``

.. image:: /images/climate/table_color.png
.. raw:: html

    <br/><br/>
    <br/><br/>

.. _climate-variant_type:
variant_type
************
   Используется для указания названия подтипа устройства-климата.

   * имя поля: ``variant_type``
   * тип объекта: ``String``
   * наличие значения: Обязательно
   * ограничение строки: Только заданные значения
   * **варианты:**
      * :ref:`climate_variant_thermostat` — базовый термостат с режимами «Включено»/«Выключено», с возможностью подключения до трёх датчиков.
      * :ref:`climate_variant_cond` — расширенный термостат с поддержкой от 2 до 5 режимов работы и от 0 до 5 допольнительных режимов, например вентиляции. Часто используется в виде Кондиционера.

.. raw:: html

    <br/><br/>


.. _climate-variant:
variant
*******
   Поле ``variant`` содержит параметры, соответствующие выбранному типу устройства (``variant_type``). Ниже приведены описания параметров для каждого из подтипов.

.. raw:: html

    <br/><br/>
    <br/><br/>
    <br/><br/>

.. _climate_variant_cond:
climate_variant_cond
-------------------

.. image:: /images/climate/climate_variant_cond.png

Расширенный термостат с поддержкой от 2 до 5 режимов работы и от 0 до 5 режимов вентиляции.

Параметры ``variant``:

* :ref:`climate_variant_cond-mode_command_topic` - Командный MQTT-топик для режимов.
* :ref:`climate_variant_cond-mode_state_topic`- MQTT-топик обратной связи для режимов.
* :ref:`climate_variant_cond-off_payload`- Команда (Сообщение) для включения.
* :ref:`climate_variant_cond-modes`- Массив режимов при включенном состоянии.
* :ref:`climate_variant_cond-currentTemp_state_topic`- MQTT-топик обратной связи текущей температуры.
* :ref:`climate_variant_cond-targetTemp_command_topic`- Командный MQTT-топик для заданной температуры (уставки).
* :ref:`climate_variant_cond-targetTemp_state_topic`- MQTT-топик обратной связи для заданной температуры (уставки).
* :ref:`climate_variant_cond-fan_command_topic`- Командный MQTT-топик для дополнительных режимов.
* :ref:`climate_variant_cond-fan_state_topic`- MQTT-топик обратной связи для дополнительных режимов.
* :ref:`climate_variant_cond-fan_modes`- Массив дополнительных режимов.

.. _climate_variant_cond-mode_command_topic:
mode_command_topic
*******************
   Командный MQTT-топик, куда отправляется сообщение из параметра ``payload`` выбранного режима, который мы хотим установить.

   :имя поля: ``mode_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"mode_command_topic":"panel/climate/1/mode_command"``


.. _climate_variant_cond-mode_state_topic:
mode_state_topic
*******************
   MQTT-топик обратной связи, откуда приходит сообщение из параметра ``payload`` с режимом, который установился.

   :имя поля: ``mode_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"mode_state_topic":"panel/climate/1/mode_state"``

.. _climate_variant_cond-off_payload:
off_payload
*******************
   Сообщение, которое отправляется на командный MQTT-топик ``mode_command_topic``, при режиме «выключено». При получении этого сообщения на MQTT-топик обратной связи ``mode_state_topic`` интерфейс обновляется на режим «выключено».

   :имя поля: ``off_payload``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"off_payload":"0"``
   :пример: ``"off_payload":"off"``

.. _climate_variant_cond-currentTemp_state_topic:
currentTemp_state_topic
*******************
   MQTT-топик обратной связи, откуда приходит сообщение с текущим значением температуры.

   :имя поля: ``currentTemp_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"currentTemp_state_topic":"panel/climate/1/currentTemp_state"``

.. _climate_variant_cond-targetTemp_command_topicc:
targetTemp_command_topic
*******************
   Командный MQTT-топик, куда отправляется сообщение с температурой, установленной пользователем .

   :имя поля: ``targetTemp_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"targetTemp_command_topic":"panel/climate/1/targetTemp_command"``

.. _climate_variant_cond-targetTemp_state_topic:
targetTemp_state_topic
*******************
   MQTT-топик обратной связи, откуда приходит сообщение с температурой, установленной устройством.

   :имя поля: ``targetTemp_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"targetTemp_state_topic":"panel/climate/1/targetTemp_state"``

.. _climate_variant_cond-fan_command_topic:
fan_command_topic
*******************
   Командный MQTT-топик, куда отправляется сообщение с режимом скорости, установленный пользователем.

   :имя поля: ``fan_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"fan_command_topic":"0"``

.. _climate_variant_cond-fan_state_topic:
fan_state_topic
*******************
   MQTT-топик обратной связи, откуда приходит сообщение с режимом скорости, установленный устройством.

   :имя поля: ``fan_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"fan_state_topic":"0"``

.. _climate_variant_cond-modes:
modes
*******************
   Массив с обозначениями режимов, которые соответствуют состоянию включенного устройства. Режим "Выкл" установлен автоматически, убрать его нельзя, можно изменить только команду ``off_payload``, который он отправляет/принимает. Массив предполагает настройку от 1 до 4 режимов (не включая режим "выкл"), а именно иконки ``icon``, названия режима ``title``, отображаемого в настройках, цвет ``color`` кругового ползунка при выборе соответствующего режима, который так же выбирается из приведенной таблицы выше, и сообщения ``payload``, которое режим отправялет/принимает в MQTT-топиках.

   :имя поля: ``modes``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения

Пример для 4-х режимов::

   "modes": {
        "mode_1": { "icon": "\uDB86\uDCF2", "title": "Авто", "color": "color_green", "payload": "auto" },
        "mode_2": { "icon": "\uDB80\uDE38", "title": "Обогрев", "color": "color_red", "payload": "heat" },
        "mode_3": { "icon": "\uDB81\uDF17", "title": "Охлаждение", "color": "color_blue", "payload": "cool" },
        "mode_4": { "icon": "\uDB81\uDD8E", "title": "Осушение", "color": "color_yellow", "payload": "dry" }
    }

Пример для 1-го режима::

   "modes": {
        "mode_1": { "icon": "\uDB80\uDE38", "title": "Обогрев", "color": "color_red", "payload": "heat" },
        "mode_2": { "icon": "", "title": "", "color": "", "payload": "" },
        "mode_3": { "icon": "", "title": "", "color": "", "payload": "" },
        "mode_4": { "icon": "", "title": "", "color": "", "payload": "" }
    }

.. raw:: html

    <br/><br/>
    <br/><br/>

.. _climate_variant_cond-fan_modes:
fan_modes
*******************
  Массив с обозначениями дополнительных режимов. Массив предполагает настройку от 0 до 5 режимов, а именно иконки ``icon`` и сообщения ``payload``, который режим отправялет/слушает в MQTT-топиках.


   :имя поля: ``fan_modes``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения

Пример для 5-ти режимов::

   "fan_modes": {
        "mode_1": { "icon": "\uDB85\uDF1D", "payload": "0" },
        "mode_2": { "icon": "\uDB85\uDC72", "payload": "1" },
        "mode_3": { "icon": "\uDB85\uDC73", "payload": "2" },
        "mode_4": { "icon": "\uDB85\uDC74", "payload": "3" },
        "mode_5": { "icon": "\uDB85\uDC72", "payload": "4" }
    }

Пример для 4-х режима::

   "fan_modes": {
        "mode_1": { "icon": "\uDB85\uDF1D", "payload": "auto" },
        "mode_2": { "icon": "\uDB85\uDC72", "payload": "speed_1" },
        "mode_3": { "icon": "\uDB85\uDC73", "payload": "speed_2" },
        "mode_4": { "icon": "\uDB85\uDC74", "payload": "speed_3" },
        "mode_5": { "icon": "", "payload": "" }
    }

Пример для климатического устройства без дополнительных режимов::

   "fan_modes": {
        "mode_1": { "icon": "", "payload": "" },
        "mode_2": { "icon": "", "payload": "" },
        "mode_3": { "icon": "", "payload": "" },
        "mode_4": { "icon": "", "payload": "" },
        "mode_5": { "icon": "", "payload": "" }
    }
    
.. raw:: html

    <br/><br/>
    <br/><br/>

.. _climate_variant_thermostat:
climate_variant_thermostat
-------------------

.. image:: /images/climate/climate_variant_thermostat.png

Базовый термостат с режимами «Включено»/«Выключено», с возможностью подключения до трёх датчиков.

Параметры ``variant``:

* :ref:`climate_variant_thermostat-OnOff_command_topic` - Командный MQTT-топик для отправки команды.
* :ref:`climate_variant_thermostat-OnOff_state_topic`- MQTT-топик обратной связи для получения состояния.
* :ref:`climate_variant_thermostat-payload_on`- Команда (Сообщение) для включения.
* :ref:`climate_variant_thermostat-payload_off`- Команда (Сообщение) для выключения.
* :ref:`climate_variant_thermostat-targetTemp_command_topic`- Командный MQTT-топик для заданной температуры (уставки).
* :ref:`climate_variant_thermostat-targetTemp_state_topic`-  MQTT-топик обратной связи для заданной температуры (уставки).
* :ref:`climate_variant_thermostat-sensor_main`- Номер главного датчика.
* :ref:`climate_variant_thermostat-sensor`- Массив с датчиками.

.. _climate_variant_thermostat-OnOff_command_topic:
OnOff_command_topic
*******************
   Командный MQTT-топик, куда отправляется сообщение о состоянии.

   :имя поля: ``OnOff_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"OnOff_command_topic":"panel/climate/2/OnOff_command"``

.. _climate_variant_thermostat-OnOff_state_topic:
OnOff_state_topic
*******************
   MQTT-топик обратной связи, откуда приходят сообщения состояния (включения и выключения).

   :имя поля: ``OnOff_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"OnOff_state_topic":"panel/climate/2/OnOff_state"``

.. _climate_variant_thermostat-payload_on:
payload_on
*******************
   Команда включения, которая отправляется на командный MQTT-топик (``OnOff_command_topic``) и если такая команда приходит на MQTT-топик обратной связи (``OnOff_state_topic``), интерфейс обновляется на состояние «включено».

   :имя поля: ``payload_on``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"payload_on":"1"``

.. _climate_variant_thermostat-payload_off:
payload_off
*******************
   Команда выключения, которая отправляется на командный MQTT-топик (``OnOff_command_topic``) и если такая команда приходит на MQTT-топик обратной связи (``OnOff_state_topic``), интерфейс обновляется на состояние «выключено».

   :имя поля: ``payload_off``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"payload_off":"0"``

.. _climate_variant_thermostat-targetTemp_command_topic:
targetTemp_command_topic
*******************
   Командный MQTT-топик, куда отправляется сообщение с установленной пользователем температурой.

   :имя поля: ``targetTemp_command_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"targetTemp_command_topic":"panel/climate/2/targetTemp_command"``

.. _climate_variant_thermostat-targetTemp_state_topic:
targetTemp_state_topic
*******************
   MQTT-топик обратной связи, откуда приходит сообщение с установленной устройством температурой.

   :имя поля: ``targetTemp_state_topic``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"targetTemp_state_topic":"panel/climate/2/targetTemp_state"``

.. _climate_variant_thermostat-sensor_main:
sensor_main
*******************
   Номер главного датчика, данные которого будут выводиться на сам блок устройства. Если датчиков нету, укажите значение ``"sensor_main":"0"``.

   :имя поля: ``sensor_main``
   :тип объекта: ``Integer``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения
   :пример: ``"sensor_main":"1"``

.. _climate_variant_thermostat-sensor:
sensor
*******************
   Массив где указываются датчики устройства. Возможно установить от 0 до 3 датчиков. В случае если не нужно отображать датчики, просто оставьте поля пустыми и в параметре ``sensor_main`` установить значение 0.

   :имя поля: ``sensor``
   :тип объекта: ``String``
   :наличие значения: Обязательно
   :ограничение строки: Нет ограничения

   Параметры полей:

   * ``icon`` — Иконка, отображаемая у датчика внутри страницы настроек.
   * ``measure`` — Обозначение, отображаемое у датчика внутри страницы настроек.
   * ``state_topic`` — MQTT-топик обратной связи, откуда приходят сообщения со значением соответствующего датчика.

Пример для 3-х датчиков::

   "sensors": {
        "sensor_1": { "icon": "\uDB81\uDFE4", "measure": "ppm", "state_topic": "panel/climate/3/sensor_1_state" },
        "sensor_2": { "icon": "\uDB81\uDD8E", "measure": "%", "state_topic": "panel/climate/3/sensor_2_state" },
        "sensor_3": { "icon": "\uDB80\uDF2A", "measure": "ppb", "state_topic": "panel/climate/3/sensor_3_state" }
    }

Пример для 1-го датчика::

   "sensors": {
        "sensor_1": { "icon": "\uDB83\uDF55", "measure": "°С", "state_topic": "panel/climate/2/sensor_1_state" },
        "sensor_2": { "icon": "", "measure": "", "state_topic": "" },
        "sensor_3": { "icon": "", "measure": "", "state_topic": "" }
    }

Пример для устройства, не имеющего дополнительные датчики::

   "sensors": {
        "sensor_1": { "icon": "", "measure": "", "state_topic": "" },
        "sensor_2": { "icon": "", "measure": "", "state_topic": "" },
        "sensor_3": { "icon": "", "measure": "", "state_topic": "" }
    }

.. _climate-full_example:
Полный пример конфигурации климатических устройств
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
                            "sensor_main": 1,
                            "sensors": {
                                "sensor_1": { "icon": "\uDB83\uDF55", "measure": "°С", "state_topic": "panel/climate/2/sensor_1_state" },
                                "sensor_2": { "icon": "", "measure": "", "state_topic": "" },
                                "sensor_3": { "icon": "", "measure": "", "state_topic": "" }
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
                            "sensor_main": 2,
                            "sensors": {
                                "sensor_1": { "icon": "\uDB81\uDFE4", "measure": "ppm", "state_topic": "panel/climate/3/sensor_1_state" },
                                "sensor_2": { "icon": "\uDB81\uDD8E", "measure": "%", "state_topic": "panel/climate/3/sensor_2_state" },
                                "sensor_3": { "icon": "\uDB80\uDF2A", "measure": "ppb", "state_topic": "panel/climate/3/sensor_3_state" }
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
                            "sensor_main": 1,
                            "sensors": {
                                "sensor_1": { "icon": "\uDB81\uDD8E", "measure": "%", "state_topic": "panel/climate/4/sensor_1_state" },
                                "sensor_2": { "icon": "", "measure": "", "state_topic": "" },
                                "sensor_3": { "icon": "", "measure": "", "state_topic": "" }
                            }
                        }
                    }
                }
            ]
        }]
    }
    
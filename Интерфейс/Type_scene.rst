Тип scene (Сценарий)
====================

Блок scene только отправляет команду на сервер при нажатии. Параметры:

* param_1: Назначение.
* param_2: Локация.
* param_3: Название.
* icon: Иконка.
* command_topic: Топик MQTT.
* payload: Сообщение, отправляемое на топик MQTT.


Подробнее про каждый параметр ниже:

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

get_random_ingredients
----------------------

.. function:: get_random_ingredients(kind=None)

   Return a list of random ingredients as strings.

   :param kind: Optional "kind" of ingredients.
   :type kind: list[str] or None
   :raises InvalidKindError: If the kind is invalid.
   :return: The ingredients list.
   :rtype: list[str]

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']


Пример::

    {
        "block": 1,
        "type": "scene",
        "data": 
        {
            "param_1": "Сцена",
            "param_2": "Гостинная",
            "param_3": "Вечеринка",
            "icon": "\uDB84\uDC56",
            "command_topic": "panel/scenes/1",
            "payload": "1"
        }
    }

Пример::

    {
        "block": 2,
        "type": "scene",
        "data": 
        {
            "param_1": "",
            "param_2": "Режим",
            "param_3": "Чтение",
            "icon": "\uDB84\uDC56",
            "command_topic": "panel/scenes/2",
            "payload": "1"
        }
    }

.. image:: /images/block_scene.png
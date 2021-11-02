---
description: сервису время, эвенту - бас
---

# Events

Не стоит использовать классы событий, базирующиеся на типе внутренних данных. Это нарушает принцип единой ответственности и, с большой вероятностью, может привести к переусложнению логики (например, при изменении/расширении класса события новыми методами и/или свойствами для одного из контекстов) или нарушению консистентности данных из-за пересечения логоки работы с данными из разных контекстов.

Класс события должен именоваться соответственно самому событию и, в идеале, должен представлять собой DTO с минимумом содержащейся информации (например, ID объекта вместо непосредственно самого объекта). Это позволит разнести ответственность и упростить работу с событием (в особенности, если используются или планируются к использованию отложенные события, внешняя шина событий, [DDD](../approaches/ddd.md) и т.п.).

Хорошие варианты классов событий:

```

class OrderBilledEvent(int $orderId) { ... }

class OrderShippedEvent(int $orderId) { ... }

```

`Типичный ошибочный вариант класса события:`

```

class OrderEvent(Order $order) { ... }

```

{% hint style="info" %}
Если в классе события используются константы и/или методы с бизнес логикой, то это один из явных признаков нарушения зоны ответственности.
{% endhint %}

``

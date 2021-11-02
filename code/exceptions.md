---
description: исключения только подтверждают правило
---

# Exceptions

Не стоит делать один класс исключения на все возможные кейсы. Гораздо нагляднее, читабельнее и удобнее использовать раздельные исключения по соответствующим типам.

Хороший вариант использования исключений:

```

throw new OrderNotFoundException();

throw new ShipmentNotFoundException();

```

Типичный вариант некорректного использования:

```

throw new ResourceNotFoundException(
    ResourceNotFoundException::MESSAGE_TYPE_ORDER_NOT_FOUND,
    ResourceNotFoundException::CODE_TYPE_ORDER_NOT_FOUND,
);

```

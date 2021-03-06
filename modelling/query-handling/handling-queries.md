---
description: Queries PHP
---

# Handling Queries

## Writing Query Handler

In `Ecotone`, an object may declare a number of query handler methods, by annotating them with the `#[QueryHandler]` attribute. 

### Class Routing

For a query handler method, the first declared parameter defines which query message object it will receive.

```php
class OrderSummary
{
    #[QueryHandler] 
    public function getOrders(GetOrdersQuery $query) : array
    {
        //return orders
    }
}
```

{% hint style="info" %}
How to publish queries, you may see in [Dispatching Queries section](dispatching-queries.md)
{% endhint %}

### Name Routing

To route `Message` to `@QueryHandler` by name we can use `routing.`   
In below example Message will be routed by `order.getOrders`.   

```php
use Ecotone\Modelling\Annotation\QueryHandler;

class OrderSummary
{
    #[QueryHandler("order.getOrders")] 
    public function getOrders(GetOrdersQuery $query) : array
    {
        //return orders
    }
}
```

{% hint style="info" %}
Query can be anything `class/scalar/array` as long as Ecotone does know how to convert it if there is a need.   
Read more in [Method Invocation and Conversion](../../messaging/conversion/)
{% endhint %}

### 


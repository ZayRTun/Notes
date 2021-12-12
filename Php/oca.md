**Home**
- [Home](../index.md)
---

# Object Composition & Abstraction

## Composition
- Object Composition is when one class has a pointer to another class where behavior is located
  - We compose this Subscription Class using Gateway
  - Composition is Typically done through the **constructor injection**

```php
<?php

class Subscription
{
    // This here is the pointer to another class
    protected StripeGateway $gateway;

    public function __construct(StripeGateway $gateway)
    {
        $this->gateway = $gateway;
    }

    public function create()
    {

    }

    public function cancel()
    {
        // To Cancel a Subscription we might
        // find stripe customer
        $customer = $this->gateway->findStripeCustomer();
        // find stripe subscription by customer
    }

    public function invoice()
    {

    }

    public function swap($newPlan)
    {

    }
}

class StripeGateway
{
    public function findStripeCustomer(): string
    {
        return 'customer';
    }

    public function findStripeSubscriptionByCustomer()
    {

    }
}
```
### Notice that **Subscription Class** is **Composed** with a **specific** billing provider
### Depending on the size of the project this may be Okay
### Stripe may be the only provider this project ever uses

#
# Abstraction
## However you just never know !!!
### The `Subscription` class should not be too depended on a Specific Billing Provider
### `Subscription` doesn't care about Stripe, it just wants Billing or a Gateway

```php
<?php

class Subscription
{
    // This here is whats known as Depending upon abstraction
    protected Gateway $gateway;

    public function __construct(Gateway $gateway)
    {
        $this->gateway = $gateway;
    }

    public function create()
    {

    }

    public function cancel()
    {
        // To Cancel a Subscription we might
        // find stripe customer
        $customer = $this->gateway->findStripeCustomer();
        // find stripe subscription by customer
    }

    public function invoice()
    {

    }

    public function swap($newPlan)
    {

    }
}
```
## Interface: Gateway Contract
```php
interface Gateway
{
    public function findCustomer();


    public function findSubscriptionByCustomer();
}
```

## Gateway Contract Implementing Classes
```php
class StripeGateway implements Gateway
{
    public function findCustomer()
    {
        // TODO: Implement findCustomer() method.
    }

    public function findSubscriptionByCustomer()
    {
        // TODO: Implement findSubscriptionByCustomer() method.
    }
}

class BraintreeGateway implements Gateway
{
    public function findCustomer()
    {
        // TODO: Implement findCustomer() method.
    }

    public function findSubscriptionByCustomer()
    {
        // TODO: Implement findSubscriptionByCustomer() method.
    }
}
```

## And now due to `abstraction` we can provide any Gateway as long as it conforms to the `Gateway Contract` and everything will work.
```php
$stripeSubscription = new Subscription(new StripeGateway());
$braintreeSubscription = new Subscription(new BraintreeGateway());
```
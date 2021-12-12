**Home**
- [Home](../index.md)
---

# Handshakes & Interface

## Simple Handshake Approach

- Duck typing the method. If it walks like a duck and quack like a duck, we are good to go.
- We are not type hinting

```php
<?php

class CampaignMonitor
{
    public function subscribe()
    {
        die('Subscribing with Campaign Monitor.');
    }
}

class Drip
{
    public function subscribe()
    {
        die('Subscribing with Drip.');
    }
}

class NewletterSubscriptionsController
{
    // Being Dynamic
    // No Type Hinting the input here
    public function store($newsletter)
    {
       $email = 'john@exm.com';
       $newsletter->subscribe($email);
    }
}

$newsletter = new NewletterSubscriptionsController();

$newsletter->store(new CampaignMonitor());
```

## A More **Formal** approach to above solution using an `Interface` a Contract.

- Interface is a Contract. Contract is adding a user to a newsletter.
- Interface is a Class without behavior, **ONLY METHOD SIGNATURES**.
- Interface does not care:
  - **HOW YOU SUBSCRIBE THE USER**
  - It doesn't care if it's local, remote or if your using a CURL Request.
- **IT ONLY CARES THAT YOU EXPOSE THE BEHAVIOR/FUNCTIONALITIES THAT YOU CAN SUBSCRIBE**

```php
<?php
interface Newsletter
{
    // Notice that there is no body here. Your only exposing the behavior.
    public function subscribe($email);
}
```

### The Class now `implements` the `Newsletter` Interface
```php
class CampaignMonitor implements Newsletter
{
    public function subscribe($email)
    {
        die('Subscribing with Campaign Monitor.');
    }
}

class Drip implements Newsletter
{
    public function subscribe($email)
    {
        die('Subscribing with Drip.');
    }
}
```

## Notice the **TYPE HINTING**
- Requires that the given Argument must implement the **Newsletter Interface**

```php
class NewsLetterSubscriptionController
{
    public function store(Newsletter $newsletter)
    {
       $email = 'john@exm.com';
       $newsletter->subscribe($email);
    }
}

$newsletter = new NewsLetterSubscriptionController();

// The CampaignMonitor now `implements` the `Newsletter` Interface
// Which Makes sure that we pass the appropriate argument
$newsletter->store(new Drip());
```

- Now we no longer have a simple handshake
- We have written down the terms of the contract
- By Implementing the `Newsletter` Interface/Contract, Class `Drip` & `CampaignMonitor` have agreed to conform to the terms of the contract.

## The difference between the previous example is that we've turned the `HANDSHAKE` into a `FORMAL CONTRACT`.

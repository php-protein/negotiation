<p align=center><img height=150 src="https://raw.githubusercontent.com/php-protein/docs/master/assets/protein-large.png"></p>

# Protein | Negotiation
## A module for handling Content Negotiation.

> See Reference : [RFC 7231](https://tools.ietf.org/html/rfc7231)

### Install
---

```
composer require proteins/negotiation
```

Require the class via :

```php
use Proteins\Negotiation;
```


### Get best match between need and offerings
---

> **Note:** You can use `*` as wildcards for matching a family of choices.


```php
$need  = 'image/*;q=0.9,*/*;q=0.2';
$offer = 'text/html,svg/xml,image/svg+xml';
echo Negotiation::bestMatch($need,$offer);
```

```
image/svg+xml
```

### Preferred and best match
---

Negotiation class automatically orders by priority based on `q` parameter.
 
```php
$negotiatior = new Negotiation('en-US;q=0.3,it,en;q=0.4,es;q=0.9,de');
```

You can obtain the preferred response via the `preferred` method.

```php
echo $negotiatior->preferred();
```

```
it
```

Or get the best match against another RFC7231 query

```php
echo $negotiatior->best('es,en-US');
```

```
es
```

`false` will be returned if no match can be found.

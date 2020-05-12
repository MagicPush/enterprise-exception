# EnterpriseException

A PHP library for large web applications exceptions management.

This readme is written in the _TL;DR_-style. There is the full-scale guide
["_HOWTO for dummies and experienced_"](https://magicpush.github.io/enterprise-exception/) (english and russian
versions) powered by GitHub Pages. Also you can access it [offline](docs/index.md).

- [What is it for](#what-is-it-for)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage or HOWTO lite edition](#usage-or-howto-lite-edition)
- [If you want to contribute](#if-you-want-to-contribute)

## What is it for

### Exceptions codes globalization

For instance your project has exception classes with identical exceptions codes:
- class _AuthException_ can throw the exception "invalid password" with the code **2**;
- class _BillingException_ can throw the exception "not enough money" with the same code **2**.

And you want those codes become unique so you could differ those exceptions while parsing logs. Or it would be handy
for your API clients' robots. If this is your case then use [GlobalException](#for-codes-globalization).

### Exceptions customization

- Do you want to specify frontend and system version of exceptions messages?
- Do you want to show your users not real exceptions messages but stubs like "_Please contact our support team to help
with the error XXXXXX_" for low-level exceptions?
- Do you want to add any other custom properties to your exceptions and handle them as you wish?

If you answered "yes" for any question then you probably would like to use
[CustomizableException](#for-exceptions-customization).

### Customized exceptions parsing

If you already use
[CustomizableException](#exceptions-customization) and have dozens of customizable exception classes then you probably
would like to:
- print a full list of your exceptions with their properties
- filter your exceptions (for instance to show only user-visible exceptions)
- validate your globalized exceptions codes

If so then you should use [Parser](#for-customizable-exceptions-parsing).

## Requirements
- Core PHP v7.0+

## Installation

There are several ways to install the library:
- Composer:

    ```
    composer require magic-push/enterprise-exception
    ```

- GIT: clone / fork / the repository, include as submodule etc.
- Download the repository (or at least the _"[/src](/src)"_ folder).

## Usage or HOWTO lite edition

Every structural element is described in its PHPDoc.

There are [example classes](examples/resources) and [demo scripts](examples) for quick features overview.
You can launch demos via CLI:

```
php examples/global.php # or any other *.php file
```

The short usage guide is:

### For codes globalization

1. Your base exception class must extend [GlobalException](src/GlobalException.php).
1. The classes you want to globalize must extend your base exception class (previously mentioned).
1. You must redefine **CLASS_CODE_LIST** constant array in your base exception class with your exception classes
qualified namespaced names as keys and their own (class) codes as values.
1. That's it! Now your exceptions have unique codes!

### For exceptions customization

That's trickier; you should read the PHPDoc or the [_HOWTO_ guide](https://magicpush.github.io/enterprise-exception/)
for better understanding. But for a start:

1. Your base exception class must extend [CustomizableException](src/CustomizableException/CustomizableException.php).
1. All the classes you want customizable exceptions for must extend your base exception class (previously mentioned).
1. You must redefine **EXCEPTIONS_PROPERTIES** constant array in each class you want customize exceptions for.
See the array PHPDoc for possible keys.
1. At this moment you must throw your exceptions with a new constructor signature: an exception code must be the first
parameter (obligatory). If the first parameter is _not_ numeric/specified then the customization config will be ignored.
1. Use corresponding methods to fully enjoy your exceptions customization!

### For customizable exceptions parsing

1. Do all the things for [exceptions customization](#for-exceptions-customization).
1. You must mention all the classes you want to be parsed in **CLASS_CODE_LIST** constant array in your base
exception class. Like for the [globalization](#for-codes-globalization), but you can specify **0** for class codes if
you don't want to use the globalization feature itself.
1. Call [Parser](src/CustomizableException/Parser.php)::parse() method with options and/or filters you desire!

## If you want to contribute

Read the [contribution guide](CONTRIBUTING.md) to know more.


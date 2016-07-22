---
layout: default
title: The User component
---

# The User component

The library provides a `User` class to ease user creation and manipulation.

## Instantiation

### Using the default constructor.

~~~php
<?php

public function __contruct($user = null)
~~~

The constructor accepts:

- a valid string according to RFC3986 rules;
- the `null` value;

#### Example

~~~php
<?php

use League\Uri\Components\User;

$user = new User('john');
echo $user->getContent();      //display 'john'
echo $user;                    //display 'john'
echo $user->getUriComponent(); //display 'john'

$user = new User();
echo $user->getContent();      //display null
echo $user;                    //display ''
echo $user->getUriComponent(); //display ''
~~~

<p class="message-warning">If the submitted value is not a valid an <code>InvalidArgumentException</code> exception is thrown.</p>

<p class="message-info">On instantiation the submitted string is normalized using RFC3986 rules.</p>

### Using a League Uri object

You can access a `User` object with an already instantiated `Uri` object.

~~~php
<?php

use League\Uri\Schemes\Http as HttpUri;

$uri = HttpUri::createFromString('http://uri.thephpleague.com:82');
$user = $uri->user; // $user is a League\Uri\Components\User object;
~~~

## Properties and Methods

The component representation, comparison and manipulation is done using the package [UriPart](/components/overview/#uri-part-interface) and the [Component](/components/overview/#uri-component-interface) interfaces methods.

### User::getValue

<p class="message-notice">New in <code>version 4.2</code></p>

~~~php
<?php

public function User::getValue(void): string
~~~

Returns the decoded string representation of the user component

#### Example

~~~php
<?php
use League\Uri\Components\User;

$user = new User('frag:ment');
$user->getContent(); // display 'frag%3Ament'
$user->getValue(); // display 'frag:ment'
~~~
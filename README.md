# Aux Utilities

### A collection of utility functions to help do things faster with PHP.


# Installation
Easy install with composer:
```
composer require hxgf/aux:0.1.0@dev
```
```php
use Aux\x;
require __DIR__ . '/vendor/autoload.php';
```



# Usage

## x::email_send($parameters)
Sends a plain text or html email using PHP mail().
```php
x::email_send([
  'to' => 'recipient@domain.com',
  'from' => 'sender@example.com',
  'cc' => 'cc-address@example.com',  // optional
  'bcc' => 'bcc-address@example.com',  // optional
  'reply-to' => 'reply-address@example.com',  // optional
  'subject' => 'Send me an email',
  'html' => true,  // optional, message will be sent as plain text unless this is true
  'message' => 'Right now...<br /><br /><br /><b><u>RIGHT NOW</u></b>'
]);
```
Messages can be sent using the Mailgun API if Mailgun credentials are available in a global settings array like this:
```php
$GLOBALS['settings']['mailgun']['api_key'] = 'key-f453654gg65sd6234r6rw5df6544e';
$GLOBALS['settings']['mailgun']['domain'] = 'notifications.example.com';
```

## x::client_ip()
Returns the address of the computer making the current request.
```php
echo x::client_ip();
```

## x::url_slug($string)
Returns a lowercase URL-safe version of a given string, substituting `-` for spaces and punctuation.
```php
echo x::url_slug('John User Name'); // john-user-name
```

## x::url_strip($url)
Removes the protocol and trailing slashes from a given url, returning only the domain name.
```php
echo x::url_strip('https://example.com/'); // example.com
```

## x::url_validate($url)
Returns a valid URL, adding `http://` if needed.
```php
echo x::url_strip('example.com'); // http://example.com
```

## x::br2nl($string)
The opposite of `nl2br()`, replaces `<br />` (and `<br>`) html tags with newline (`\n`) character.
```php
echo x::br2nl('This is a <br /> multi-line <br /> string!'); // This is a \n multi-line \n string!
```

## x::array_encode()
Turns an array of strings into a single string, separated by a vertical bar (`|`) character.
```php
echo x::array_encode(['Peter', 'Paul', 'Ringo', 'George']); // Peter|Paul|Ringo|George
```

## x::array_decode()
Turns a string separated by a vertical bar (`|`) character into an array of strings.
```php
$people = x::array_decode('Peter|Paul|Ringo|George');
print_r($people); // ['Peter', 'Paul', 'Ringo', 'George']
```

# PHP

## Tip
### ?? vs ?:
```php
unset($a);
echo '?? = '. ( $a ?? 'abc' ) ."\n";	// ?? = abc     with PHP Notice
echo '?: = '. ( $a ?: 'abc' ) ."\n";	// ?: = abc     with PHP Notice
```
```php
$a = null;
echo '?? = '. ( $a ?? 'abc' ) ."\n";	// ?? = abc
echo '?: = '. ( $a ?: 'abc' ) ."\n";	// ?: = abc
```
```php
$a = false;
echo '?? = '. ( $a ?? 'abc' ) ."\n";	// ?? =         only unset or null
echo '?: = '. ( $a ?: 'abc' ) ."\n";	// ?: = abc     detect false
```
```php
$a = '';
echo '?? = '. ( $a ?? 'abc' ) ."\n";	// ?? =         only unset or null
echo '?: = '. ( $a ?: 'abc' ) ."\n";	// ?: = abc     detect empty String
```
```php
$a = '    ';
echo '?? = '. ( $a ?? 'abc' ) ."\n";	// ?? =
echo '?: = '. ( $a ?: 'abc' ) ."\n";	// ?: =
```
```php
$a = 'bbc';
echo '?? = '. ( $a ?? 'abc' ) ."\n";	// ?? = bbc
echo '?: = '. ( $a ?: 'abc' ) ."\n";	// ?: = bbc
```
```php
$a = [];
echo '?? = '. ( $a ?? 'abc' ) ."\n";	// ?? = Array   only unset or null
echo '?: = '. ( $a ?: 'abc' ) ."\n";	// ?: = abc     detect empty Array
```
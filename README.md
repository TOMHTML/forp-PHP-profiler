!under development!

[![Build Status](https://secure.travis-ci.org/aterrien/forp.png)](http://travis-ci.org/aterrien/forp)

# Introduction #

forp is a lightweight PHP extension which provides duration and memory profiling datas. forp is non intrusive, it provides PHP annotations to complete its work.

## PHP functions ##
- forp_start(<flags>) : start forp collector
- forp_end() : stop forp collector
- forp_dump() : return stack as flat array
- forp_print() : display forp stack (SAPI CLI)

## forp_start() flags ##

- FORP_FLAG_CPU : activate duration collect
- FORP_FLAG_MEMORY : activate memory collect
- FORP_FLAG_ANNOTATIONS : activate annotations handling

## php.ini options ##

- forp.max_nesting_level : default 50
- forp.no_internals : default 0

## Annotations  ##

- @ProfileGroup

Sets groups that function belongs.

```php
/**
 * @ProfileGroup("data loading","rendering")
 */
function exec($query) {
    /* ... */
}
```

- @ProfileCaption

Adds caption to function. Caption string may contain references (#<param num>) to parameters of the function.

```php
/**
 * @ProfileCaption("Find row for pk #1")
 */
public function findByPk($pk) {
    /* ... */
}
```

- @ProfileAlias

Gives an alias name to a function. Useful for anonymous functions

```php
/**
 * @ProfileAlias("MyAnonymousFunction")
 */
$fn = function() {
    /* ... */
}
```

- @ProfileHighlight

Adds a frame around output generated by the function.

```php
/**
 * @ProfileHighlight("1")
 */
function render($datas) {
    /* ... */
}
```

## Linux Install ##

* make
```sh
git clone https://github.com/aterrien/forp
cd forp
phpize
./configure
make
make test
make install
```

* php.ini
```ini
extension=forp.so
```

## Win32 Install ##

For PHP 5.3 - Thread Safe (by default) :
https://github.com/downloads/ichiriac/forp/php53_x86_ts_forp.dll

For PHP 5.3 - Non Thread Safe :
https://github.com/downloads/ichiriac/forp/php53_x86_nts_forp.dll


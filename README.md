![PHP](https://upload.wikimedia.org/wikipedia/commons/2/27/PHP-logo.svg)

# Coro PHP extension

`Coro` is a experimental `php` extension which provides coroutine feature like `lua` for php7. 

If u like it, just give me a star. thx~

## Requirements

* PHP 7.4+

## Installation

    phpize
    ./configure
    make
    make test
    make install

Add the following line to your `php.ini`

    extension=coro.so

To try out the extension, you can run the following command

    php -a -d extension=modules/coro.so

## Basic Usage

### `Coro::create`

Create a coroutine and return it. Ths parameter's type should be callable.
It's always used with `Coro::resume` , for waking the coroutine up.

### `Coro::resume`

Resume the coroutine, and it's always used with create function.

### `Coro::yield`

Yield function will suspend the coroutine, and sets coroutine to a suspended state.
It can have many useful effects when used with resume.

### `Coro::status`

Return the status of coroutine. 
There are 3 status for a coroutine:  dead, suspended, and running.

### `Coro::wrap`

Create a coroutine and return it as a callable generator like php. 

### `Coro::running`

Return currently running coroutine id.
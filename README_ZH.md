![PHP](https://upload.wikimedia.org/wikipedia/commons/2/27/PHP-logo.svg)

# Coro PHP扩展

`Coro` 是一个实验性质的`php`扩展, 提供了类似于`lua` 的非对称协程机制, 赋能现代PHP.

喜欢的话请给个小星星吧~

## 版本要求

* PHP 7.4+

## 安装

    phpize
    ./configure
    make
    make test
    make install

在 `php.ini` 新增下面的配置:

    extension=coro.so

或者如果是想简单测试的话:

    php -a -d extension=modules/coro.so

## 使用

### `Coro::create`

创建 `coroutine`，返回 `coroutine`， 参数是一个函数，当和 `resume` 配合使用的时候就唤醒函数调用

### `Coro::resume`

重启 `coroutine`，和`create`配合使用

### `Coro::yield`

挂起 `coroutine`，将 `coroutine` 设置为挂起状态，这个和 `resume` 配合使用能有很多有用的效果

### `Coro::status`

查看 `coroutine` 的状态
注：`coroutine` 的状态有三种：dead，suspended，running，

### `Coro::wrap`

创建 `coroutine`，返回一个函数，一旦你调用这个函数，就进入 `coroutine`，和 `create` 功能重复

### `Coro::running`

返回正在跑的 `coroutine`，一个 `coroutine` 就是一个线程，当使用`running`的时候，就是返回一个 `corouting` 的线程号
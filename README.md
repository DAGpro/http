<p align="center">
    <a href="https://github.com/yiisoft" target="_blank">
        <img src="https://yiisoft.github.io/docs/images/yii_logo.svg" height="100px" alt="Yii">
    </a>
    <h1 align="center">Yii HTTP</h1>
    <br>
</p>

[![Latest Stable Version](https://poser.pugx.org/yiisoft/http/v)](https://packagist.org/packages/yiisoft/http)
[![Total Downloads](https://poser.pugx.org/yiisoft/http/downloads)](https://packagist.org/packages/yiisoft/http)
[![Build status](https://github.com/yiisoft/http/actions/workflows/build.yml/badge.svg)](https://github.com/yiisoft/http/actions/workflows/build.yml)
[![Code Coverage](https://codecov.io/gh/yiisoft/http/branch/master/graph/badge.svg)](https://codecov.io/gh/yiisoft/http)
[![Mutation testing badge](https://img.shields.io/endpoint?style=flat&url=https%3A%2F%2Fbadge-api.stryker-mutator.io%2Fgithub.com%2Fyiisoft%2Fhttp%2Fmaster)](https://dashboard.stryker-mutator.io/reports/github.com/yiisoft/http/master)
[![static analysis](https://github.com/yiisoft/http/workflows/static%20analysis/badge.svg)](https://github.com/yiisoft/http/actions?query=workflow%3A%22static+analysis%22)

The package provides:

- Constants for HTTP protocol headers, methods and statuses. All along with short descriptions and RFC links.
- PSR-7, PSR-17 PhpStorm meta for HTTP protocol headers, methods and statuses.
- `ContentDispositionHeader` that has static methods to generate `Content-Disposition` header name and value.
- `HeaderValueHelper` that has static methods to parse the header value parameters.

## Requirements

- PHP 7.4 or higher.
- `mbstring` PHP extension.

## Installation

The package could be installed with [Composer](https://getcomposer.org):

```shell
composer require yiisoft/http
```

## Method constants

Individual HTTP methods could be referenced as

```php
use Yiisoft\Http\Method;

Method::GET;
Method::POST;
Method::PUT;
Method::DELETE;
Method::PATCH;
Method::HEAD;
Method::OPTIONS;
```

To have a list of these, use:

```php
use Yiisoft\Http\Method;

Method::ALL;
```

## HTTP status codes

Status codes could be referenced by name as:

```php
use Yiisoft\Http\Status;

Status::NOT_FOUND;
```

Status text could be obtained as the following:

```php
use Yiisoft\Http\Status;

Status::TEXTS[Status::NOT_FOUND];
```

## `ContentDispositionHeader` usage

`ContentDispositionHeader` methods are static so usage is like the following:

```php
use Yiisoft\Http\ContentDispositionHeader;

$name = ContentDispositionHeader::name();

$value = ContentDispositionHeader::value(
    ContentDispositionHeader::INLINE,
    'avatar.png',
);

$value = ContentDispositionHeader::inline('document.pdf');

$value = ContentDispositionHeader::attachment('document.pdf');
```

## `HeaderValueHelper` usage

`HeaderValueHelper` provides the following static methods:

```php
use Yiisoft\Http\HeaderValueHelper;

// Result: ['a' => '1', 'b' => '2']
HeaderValueHelper::getParameters('a=1;b=2');

// Result: ['value', 'a' => '1', 'b' => '2']
HeaderValueHelper::getValueAndParameters('value;a=1;b=2'));

// Result: [['value2', 'q' => 1.0], ['value1', 'q' => 0.2]]
HeaderValueHelper::getSortedValueAndParameters('value1;q=0.2,value2'));

// Result: ['text/xml', 'text/html']
HeaderValueHelper::getSortedAcceptTypes('text/html;q=0.2,text/xml;q=0.4'));
```

## PSR-7 and PSR-17 PhpStorm meta

The package includes PhpStorm meta-files that help IDE to provide values when completing code in cases such as:

```php
use Psr\Http\Message\ResponseFactoryInterface;
use Psr\Http\Message\ResponseInterface;
use Yiisoft\Http\Header;
use Yiisoft\Http\Status;

class StaticController
{
    private ResponseFactoryInterface $responseFactory;

    public function actionIndex(): ResponseInterface
    {
        return $this->responseFactory
            ->createResponse()
            ->withStatus(Status::OK)
            ->withoutHeader(Header::ACCEPT);
    }
}
```

## Documentation

- [Internals](docs/internals.md)

If you need help or have a question, the [Yii Forum](https://forum.yiiframework.com/c/yii-3-0/63) is a good place for
that. You may also check out other [Yii Community Resources](https://www.yiiframework.com/community).

## License

The Yii HTTP is free software. It is released under the terms of the BSD License.
Please see [`LICENSE`](./LICENSE.md) for more information.

Maintained by [Yii Software](https://www.yiiframework.com/).

## Support the project

[![Open Collective](https://img.shields.io/badge/Open%20Collective-sponsor-7eadf1?logo=open%20collective&logoColor=7eadf1&labelColor=555555)](https://opencollective.com/yiisoft)

## Follow updates

[![Official website](https://img.shields.io/badge/Powered_by-Yii_Framework-green.svg?style=flat)](https://www.yiiframework.com/)
[![Twitter](https://img.shields.io/badge/twitter-follow-1DA1F2?logo=twitter&logoColor=1DA1F2&labelColor=555555?style=flat)](https://twitter.com/yiiframework)
[![Telegram](https://img.shields.io/badge/telegram-join-1DA1F2?style=flat&logo=telegram)](https://t.me/yii3en)
[![Facebook](https://img.shields.io/badge/facebook-join-1DA1F2?style=flat&logo=facebook&logoColor=ffffff)](https://www.facebook.com/groups/yiitalk)
[![Slack](https://img.shields.io/badge/slack-join-1DA1F2?style=flat&logo=slack)](https://yiiframework.com/go/slack)

# Parsedown extension for Twig
For use with [Parsedown](https://github.com/erusev/parsedown) and [Twig](https://twig.symfony.com)

## Install with Composer
Add the following to your `composer.json` file:
```
"parsedown/twig": "~1.1"
```

Or, Install the Composer package:
```
composer require erusev/parsedown
```

## Activate the Parsedown filter

```php
$twig = new Twig_Environment($loader);
$twig->addExtension(new \Parsedown\Extension\ParsedownExtension());
```

## Using Parsedown with Twig

Once installed, the Parsedown filter is accessed through the name `parsedown`:

```twig
{{ 'My **favorite** markdown parser is [Parsedown](http://parsedown.org)'|parsedown }}
```

You may apply a filter to a larger section of content like this:

```twig
{% filter parsedown %}
[Parsedown][Parsedown] provides many great features:

* No Dependencies
* [Super Fast](http://parsedown.org/speed)
* Extensible
* [GitHub flavored](https://help.github.com/articles/github-flavored-markdown)
* [Tested](http://parsedown.org/tests/) in 5.3 to 7.2 and in HHVM
* [Markdown Extra extension](https://github.com/erusev/parsedown-extra)

[Parsedown]: https://parsedown.org
{% endfilter %}
```

A `parsedown()` function is also made available by the extension.

```twig
{{ parsedown('When it ~~passes tests~~ _works for you_, commit.') }}
```

## Security

If you will be parseing user-generated content, make sure to read the 
[security](https://github.com/erusev/parsedown#security) note for Parsedown. 
You should also strongly consider employing defence-in-depth measures, like [deploying a Content-Security-Policy][csp]

[csp]: https://scotthelme.co.uk/content-security-policy-an-introduction/

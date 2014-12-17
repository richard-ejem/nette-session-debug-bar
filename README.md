#Session-DebugBar ([WTFPL](http://en.wikipedia.org/wiki/WTFPL))#
Pavel Železný (2bfree), 2013 ([www.pavelzelezny.cz](http://www.pavelzelezny.cz))

## Requirements ##

[Nette Framework 2.0.12](http://nette.org) or higher. (PHP 5.3 edition)

## Documentation ##

Simple DebugBar to show content of session.

## Instalation ##

Prefered way to intall is by [Composer](http://getcomposer.org)

	{
		"require":{
			"zeleznypa/nette-session-debug-bar": "dev-master"
		}
	}

## Setup ##

To load SessionPanel into the DebugBar by insert following code into config.neon

```neon
common:
	services:
		sessionPanel:
			class: \Zeleznypa\Nette\Diagnostics\SessionPanel
			arguments:
				- @application
				- @session

	nette:
		debugger:
			strictMode: true
			bar:
				- @sessionPanel
```

You can also specify section to hide in debugbar by add setup section in service definition.

```neon
common:
	services:
		sessionPanel:
			class: \Zeleznypa\Nette\Diagnostics\SessionPanel
			setup:
				- hideSection('Nette.Http.UserStorage/')
				- hideSection('Nette.Forms.Form/CSRF')
			arguments:
				- @application
				- @session
```
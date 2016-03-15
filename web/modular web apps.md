
Npm modules

* yo-yo
* hyperscript
* hyperx
* bel
* mercury


### yo-yo by max odgen.
https://github.com/maxogden/yo-yo

Tagged template literals

Es donde uno pone una funcion enfrente de la expresión :

function doSomething () {}

doesNothing`im a string`

La diferencia está en que
a la función le llegan:

["im a string", raw:"im a string"]

function logArguments(a,b,c,d) {
	console.log(a, b, c, d)
}

var name = 'bob'
logArguments`hello ${name}!`

ene este caso se produce el tagged template array:
["hello", "!", raw:["hello", "!"]] "bob" undefined undefined

es decir que se recibe como primer argumento el array
de todas las cadenas, y el resto de argumentos son los valores interpolados del resto de las cadenas

## Módulo bel

https://github.com/shama/bel/wiki


Sigue la filosofia de data down, actions up.
la idea es poder tener modulos sencillos y distribuirlos de manera independiente:

var breadcrumb = require('breadcrumb-element')
document.querySelector('.app').appendChild(breadcrumb([1, 2, 3]))


ej>

function button (label, action) {
  return bel`<button onclick=${function () {
    action('clicked', label)
  }} oncontextmenu=${function (e) {
    e.preventDefault()
    action('menu', e.target)
  }}>${label}</button>`
}

var element = button('click me', function (name, item) {
  console.log('do ' + name + ' action')
})

## Mercury

Modular framework
de raynos.

```
	'use strict';

	var document = require('global/document');
	var hg = require('mercury');
	var h = require('mercury').h;

	function App() {
	    return hg.state({
	        value: hg.value(0),
	        channels: {
	            clicks: incrementCounter
	        }
	    });
	}

	function incrementCounter(state) {
	    state.value.set(state.value() + 1);
	}

	App.render = function render(state) {
	    return h('div.counter', [
	        'The state ', h('code', 'clickCount'),
	        ' has value: ' + state.value + '.', h('input.button', {
	            type: 'button',
	            value: 'Click me!',
	            'ev-click': hg.send(state.channels.clicks)
	        })
	    ]);
	};

	hg.app(document.body, App(), App.render);
```

Pues esta muy chevere tiene el mismo concepto de
hyperscript.

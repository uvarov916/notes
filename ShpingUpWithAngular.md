# Angular.js

BDD - Behavior Driven Development

TDD - Test Driven Development

**Angular** - a client-side JavaScript Framework for adding interactivity to HTML.

- **Directives** - HTML annotations that trigger JavaScript behaviors
- **Modules** - Where our application components live
- **Controllers** - Where we add application behavior
- **Expressions** - How values get displayed within the page


## Directives

A very basic example of using Angular directives (not practical in real prooject):
```html
<!doctype html>
<html>
	<body ng-controller="StoreController">
		...
	</body>
</html>
```
```javascript
function StoreController() {
	alert('Welcome, Ivan!');
}
```

```html
<!-- shows button if product.canPurchase equals to true -->
<button ng-show="store.product.canPurchase">Add to Cart</button>
<!-- hides div if product.soldOut equals to true -->
<div ng-hide="store.product.soldOut">...</div>
```

### Ng-repeat
```html
<body ng-controller="StoreController as store">
	<div ng-repeat="product in store.products">
		<h1> {{product.name}} </h1>
		<h2> {{product.price}} </h2>
		<button ng-show="product.canPurchase">Add to Cart</button>
	</div>
	...
</body>
```

## Modules

```javascript
// creates a module with name 'store' 
// and 0 dependencies (second argument)
var app = angular.module('store', [ ]);
```
```html
<!-- Run this module when document loads -->
<html ng-app="store">
```

## Expressions
```html
<p>I am {{4 + 6}}</p>
<!-- renders as: -->
<p>I am 10</p>
```
```html
<p>{{"hello" + " you"}}</p>
<!-- renders as: -->
<p>hello you</p>
```

## Controllers
```javascript
(function() {
	var app = angular.module('store', [ ]);
	
	app.controller('StoreController', function() {
		this.product = gem;
	});
	
	var gem = {
		name: 'Dodecahedron',
		price: 2.95,
		description: '...'
	}
})();
```
```html
<body>
	<div ng-controller="StoreController as store">
		<h1> {{store.product.name}} </h1>
		<h2> {{store.product.price}} </h2>
		<p> {{store.product.description}} </p>
	</div>
	<script type="text/javascript" src="angular.min.js"></script>
	<script type="text/javascript" src="app.js"></script>
</body>
```
# liquidless

Shopify's Liquid template engine, but less powerful. Perfect for configuration files

## Get Started

Install the dependency from npm:

```sh
npm i liquidless
```

Import the `renderTemplate` function

```js
import { renderTemplate } from 'liquidless'
```

## Usage

**Example: Rendering a string**

```js
renderTemplate('Hello, {{ world }}', { world: 'world!' }
```

Outputs:

```
Hello, world!
```

**Example: Using filters**

```js
renderTemplate('Hello, {{ world | upcase }}', { world: 'world!' }
```

Outputs:

```
Hello, WORLD!
```

**Example: Supplying custom filters**

```js
renderTemplate('Hello, {{ world | something: 1, 2, 3 }}', { world: 'world!' }, {
  filters: {
    something: (value, args, variable) => `${value} ${args.join(', ')} (${variable})`
  }
})
```

Outputs:

```
Hello, world 1, 2, 3!
```

**Example: Rending values in an object**

```js
renderTemplate([{'hello': {'world': '{{ world }}'}}], { world: 'world!' })
```

Outputs

```js
[ { hello: { world: 'world!' } } ]
```

## Filters

- `upcase` - converts each character of a string to uppercase
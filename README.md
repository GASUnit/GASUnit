[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

# GASUnit
Testing library for Google Apps Script.
Result will be logged to Logger, or posted to Slack.

## Usage
### Add library
project key: `MSnMmw8hLWgjUG6uKSTQBEzVZgzu5bsVr`

### Use Logger
```js
function reverse (text) {
  return text.split('').reverse().join('')
}
```

```js
var test = GASUnit.test
var assert = GASUnit.assert
  
function test_reverse () {
  // This test will success.
  test('reverse() returns reversed text', function () {
    assert(reverse('Hello') === 'olleH')
  })

  // This test will fail.
  test('reverse() returns reversed text', function () {
    assert(reverse('Hello') === 'Hello')
  })
}
```

#### Result
![logger.png](logger.png)

### Use Slack
```js
function reverse (text) {
  return text.split('').reverse().join('')
}
```

```js
var test = GASUnit.slack('https://...')
var assert = GASUnit.assert

function test_reverse () {
  // This test will success.
  test('reverse() returns reversed text', function () {
    assert(reverse('Hello') === 'olleH')
  })

  // This test will fail.
  test('reverse() returns reversed text', function () {
    assert(reverse('Hello') === 'Hello')
  })
}
```

If you're publishing source code, should **not** write webhook url as a literal.
You can use properties as environment variables.

```js
var test = GASUnit.slack(PropertiesService.getScriptProperties().getProperty('WEBHOOK_URL'))
var assert = GASUnit.assert

function test_reverse () {
  // This test will success.
  test('reverse() returns reversed text', function () {
    assert(reverse('Hello') === 'olleH')
  })

  // This test will fail.
  test('reverse() returns reversed text', function () {
    assert(reverse('Hello') === 'Hello')
  })
}
```

#### Result
![slack.png](slack.png)

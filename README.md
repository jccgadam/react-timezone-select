# 🌐⌚ react-timezone-select

[![Bundlephobia](https://badgen.net/bundlephobia/minzip/react-timezone-select?style=flat-square)](https://bundlephobia.com/result?p=react-timezone-select@0.8.3)
[![NPM Downloads](https://img.shields.io/npm/dm/react-timezone-select?style=flat-square)](https://www.npmjs.com/package/react-timezone-select)
[![npm](https://img.shields.io/npm/v/react-timezone-select?style=flat-square)](https://www.npmjs.com/package/react-timezone-select)
[![GitHub issues](https://img.shields.io/github/issues/ndom91/react-timezone-select?style=flat-square)](https://github.com/ndom91/react-timezone-select/issues)
[![Test CI](https://github.com/ndom91/react-timezone-select/workflows/Tests%20CI/badge.svg)](https://github.com/ndom91/react-timezone-select/actions?query=workflow%3A%22Tests+CI%22)
[![MIT](https://badgen.net/badge/license/MIT/blue?style=flat-square)](https://github.com/ndom91/react-timezone-select/blob/main/LICENSE)

Another react timezone select component, I know.. However this one has a few key benefits!

While looking around for a good option, I had trouble finding a timezone select components which:

1\) Adjusted the choices automatically with Daylight Savings Time (DST)  
2\) Didn't have a huge list of choices to scroll through when technically only 24 (ish) are necessary

> Update: **v0.7+** now built with [`spacetime`](https://github.com/spencermountain/spacetime) instead of [`moment.js`](https://momentjs.com), reducing bundle size by **~66%**!

> Update: **v0.10.1+** we're now built with Typescript!

#### Demo: [ndom91.github.io/react-timezone-select](https://ndom91.github.io/react-timezone-select/)

This demo is also available in the `./examples` directory. Simply run `npm start` after installing everything and webpack dev server should begin, where you will be able to find the demo locally at `localhost:3001`.

There is another Demo available on [Codesandbox](https://codesandbox.io/s/react-timezone-select-usage-z37hf) showing how to adjust the timezone of a selected `spacetime` object, like how one might use this in a real app.

## 🏗️ Installing

```bash
npm install react-timezone-select
```

## 🔭 Usage

```jsx
import React, { useState } from 'react'
import ReactDOM from 'react-dom'
import TimezoneSelect from 'react-timezone-select'

const App = () => {
  const [selectedTimezone, setSelectedTimezone] = useState({})

  return (
    <div className='App'>
      <h2>react-timezone-select</h2>
      <blockquote>Please make a selection</blockquote>
      <div className='select-wrapper'>
        <TimezoneSelect
          value={selectedTimezone}
          onChange={setSelectedTimezone}
        />
      </div>
      <h3>Output:</h3>
      <div className='code'>
        <pre
          style={{
            margin: '0 20px',
            fontWeight: 500,
            fontFamily: 'monospace',
          }}
        >
          {JSON.stringify(selectedTimezone, null, 2)}
        </pre>
      </div>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## 🕹️ Props

- `value` - `{ value: string, label: string }`
- `onBlur` - `() => void`
- `onChange` - `(timezone) => void`
  - Where `timezone` is, for example:
  ```
   {
     value: 'America/Juneau'
     label: '(GMT-8:00) Alaska'
   }
  ```
- `labelStyle` - `'original' | 'altName' | 'abbrev'`
- `timezone` - Custom Timezone Object - see more below
- Any other [`react-select`](https://github.com/jedwatson/react-select#props) props

## 🕒 Custom Timezones

Available in `v0.9.11+` - we've shipped a new prop to allow users to fully replace the timezone choices, or simply append custom choices of their own.

The prop `timezones` takes an object where the key/value format is: `'Official Timezone Name' : 'Your Label for it'`, don't worry we'll prepend the `(GMT ...)` part - just pass the city(s) you want to display.

For example:

```
import TimezoneSelect, { i18nTimezones } from 'react-timezone-select'
...

<TimezoneSelect
  value={selectedTimezone}
  onChange={setSelectedTimezone}
  timezones={{
     ...i18nTimezones,
    'America/Lima': 'Pittsburgh',
    'Europe/Berlin': 'Frankfurt',
  }}
/>
```

Here you can see how to append two new choices to the existing ones (`i18nTimezones`). You can also omit the `i18nTimezones` object in the prop and pass your own completely custom list of timezone choices.

## 🚧 Contributing

Pull requests are always welcome!

## 🙏 Thanks

- [All Contributors](https://github.com/ndom91/react-timezone-select/graphs/contributors)
- [Carlos Matallin](https://github.com/matallo/)
- [spacetime](https://github.com/spencermountain/spacetime)
- [react-select](https://react-select.com)

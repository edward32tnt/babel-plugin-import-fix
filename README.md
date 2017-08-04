# babel-plugin-import-fix


alter import module to certain module file path for smaller bundle file and better performance

-------

```javascript
import {Button} from 'antd';
```

after fix:

```javascript
import {Button} from 'antd/lib/button';
import 'antd/lib/button/style'
```
these fixies are made on ast.
bundle file size decrease from 1.5Mb to 286Kb.

-------

## how to use

```bash
npm install babel-plugin-import-fix -D
```

config it in your .babelrc

.babelrc
```javascript
{
  "presets": [
    ["es2015", { "modules": false }], "react"
  ],
  "plugins": ["import-fix"]
}
```

-------

## supported framework

| framework | status  |
| :------------ |:---------------:|
| xcui         |✅        |
| antd         |✅        |
| elementUI    |✅        |
| material-ui  |✅        |
| d3           |✅        |
-------

## default config:

```javascript
[
  {
    'libraryName': 'antd',
    'libraryDirectory': 'lib', 
    'style': true
  },
  {
    'libraryName': 'material-ui',
    'libraryDirectory': '',
    'camel2DashComponentName': false
  },
  {
    'libraryName': 'xcui',
    'libraryDirectory': 'lib'
  },
  {
    'libraryName': 'elementUI',
    'libraryDirectory': 'libs'
  },
  {
    'libraryName': 'd3',
    'libraryDirectory': 'components'
  }
]
```

-------

## extend usage:

you can overwrite the config or add new config like this:

.babelrc
```javascript
{
  "presets": [
    ["es2015", { "modules": false }], "react"
  ],
  "plugins": [["import-fix", [
    {
      'libraryName': 'antd',
      'libraryDirectory': 'lib', 
      'style': false
    }
  ]]]
}
```
-------

## thanks:

https://github.com/ant-design/babel-plugin-import

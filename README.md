# antd-mobile-customicon

## 安装 svg-sprite-loader

```
npm i svg-sprite-loader --save
```

该插件用来根据导入的 svg 文件自动生成 symbol 标签并插入至 html 中。

## 配置 .roadhogrc.js

```
const svgSpriteLoaderDirs = [
  require.resolve('antd-mobile').replace(/warn\.js$/, ''), // antd-mobile 内置 svg
  path.resolve(__dirname, 'src/assets'),  // 业务代码本地私有 svg 存放目录
];

export default {
  // ...
  svgSpriteLoaderDirs,
  // ...
}
```

## 定义 CustomIcon 组件

```
const CustomIcon = ({ type, className = '', size = 'md', ...restProps }) => (
  <svg
    className={`am-icon am-icon-${type.default.id} am-icon-${size} ${className}`}
    {...restProps}
  >
    <use xlinkHref={`#${type.default.id}`}/>
  </svg>
);

export default CustomIcon;
```

## 使用 CustomIcon 组件

```
<CustomIcon type={require('../assets/my-custom-icon.svg')} />
```

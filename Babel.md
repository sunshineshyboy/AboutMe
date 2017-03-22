# Babel
> 转码器，可将ES6代码转为ES5代码

```
// 转码前
input.map(item => item + 1);

// 转码后
input.map(function (item) {
  return item + 1;
});
```

## 配置文件
> .babelrc
```
{
  "presets": [], // 转码规则
  "plugins": []  // 插件
}
```

> presets : 
> > es2015 react  
    stage-0,stage-1,stage-2,stage-3(ES7中4个阶段的语法提案)  
    eg : "presets": ["es2015", "stage-2"]
    
# babel-polyfill  
> Babel默认只转换新的JavaScript句法（syntax），而不转换新的API  
  ES6在Array对象上新增了Array.from方法。Babel就不会转码这个方法。  
  如果想让这个方法运行，必须使用babel-polyfill，为当前环境提供一个垫片

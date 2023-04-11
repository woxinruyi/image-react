# canvas-to-react

canvas图片标注工具  

<!-- [demo](https://codesandbox.io/s/throbbing-dust-tyn5wk?file=/index.html) | [效果](https://tyn5wk.csb.app/) -->
[demo](https://codesandbox.io/s/boring-banach-tfpz34?file=/index.html) 

![example_lhizmZ](https://i.328888.xyz/2023/03/22/1ly1H.png)

## 简介
- 支持ts类型:可以获取实例对应的ts类型。

- 标注操作:支持矩形标注、多边形、点标注；支持拖拽、缩放;支持添加、编辑标签。

- 图片和点集位置:图片和位置点集自动铺满画布。

- 样式自定义:支持全局样式设置，框选文字颜色字体大小设置。

- 放大缩小:支持画布等比例放大缩小。

- 标签唯一性:每个标签都有自动生成的uuid

- 快捷键删除:支持delete和Backspace快捷键删除图片标签

## 1、使用

- 创建实例，设置实例化传参指定需要创建形状类型。

- 创建矩形时，按住鼠标左键拖动完成创建。

- 创建多边形时，鼠标左键单击添加点，双击闭合完成创建，`Escape`退出创建，`Backspace`退一步删除选择点。

- 按住鼠标右键拖动画布。

- 鼠标滚轮缩放画布。

- 选中形状，`Backspace`删除、`delete`快捷键删除

- 通过 instance.dataset 查看标注结果

支持 UMD 模块规范

```
npm i canvas-to-react
``` ts中引用方式
import CanvasToReact from 'canvas-to-react';
const canvasSelect = new CanvasToReact(
        boxRef.current,
        'https://www.zhuhailiang.com/api/images/onepiece.png',
      );
```


## 1、实例属性

对任意属性的修改都需要调用`instance.update()`更新视图

| 属性名称          |   类型    |         默认值         | 单个形状属性修改 |     说明     |
| ----------------- |:-------:|:-------------------:| :--------------: |:----------:|
| lock              | boolean |        false        |                  |   是否锁定画布   |
| MIN_WIDTH         | number  |         10          |                  |   最小矩形宽度   |
| MIN_HEIGHT        | number  |         10          |                  |   最小矩形高度   |
| strokeStyle       | string  |   rgb(0, 0, 255)    |       支持       |   形状边线颜色   |
| fillStyle         | string  | rgba(0, 0, 255,0.1) |       支持       |   形状填充颜色   |
| activeStrokeStyle | string  |        #f00         |                  | 选中的形状边线颜色  |
| ctrlFillStyle     | string  |        #fff         |                  |  控制点填充颜色   |
| ctrlRadius        | number  |          5          |                  |   控制点半径    |
| pointRadius        | number  |          5          |                  |    圆半径     |
| currentLabel        | number  |          5          |                  |    默认填充标签值     |
| labelFillStyle    | string  |        #fff         |       支持       | label 填充颜色 |
| labelFontSize        | number  |          12          |                  | label文字大小  |
| labelFontColor    | string  |        #000         |       支持       | label 文字颜色 |
| labelMaxLen       | number  |          5          |                  |    label 字符最大显示个数，超出字符将用...表示    |
| rollScal          | boolean | true  |                  |             是否允许滚轮缩放             |
| createType        | boolean |   0   |                  |    0 不创建，1 创建矩形，2 创建多边形，3 点标注    |
| zoomCenter          | String  | canvasCenter  |                  | 缩放中心（canvasCenter 画布中心，mouse 鼠标） |

## 2、实例方法

| 方法名称      | 参数类型 |                 说明                  |
| ------------- | :------: | :-----------------------------------: |
| setImage      |  string  |             添加/切换图片             |
| setData       |  Array   |             加载初始数据              |
| setScale      | boolean  |     true 放大画布，false 缩小画布     |
| fitZoom       |    无    |      适配图片到画布 （contain）       |
| update        |    无    | 更新画布， 修改实例属性后要执行此方法 |
| deleteByIndex |  number  |           根据索引删除形状            |

## 3、事件

| 事件名称 | 回调参数 |        说明        |
| -------- | :------: | :----------------: |
| select   |   info   |   当前选中的数据   |
| add      |   info   |   当前添加的数据   |
| delete   |   info   |   当前删除的数据   |
| updated  |   info   | 发生变化的形状数据 |
| load     |    无    |    图片加载完成    |
| error    |  error   |      错误信息      |

## 3、快捷键事件
| 事件名称 | 回调参数 |        说明        |
| -------- | :------: | :----------------: |
| 'Escape', 'Backspace','Delete' |   删除标签   |   当前选中的标签   |

## 引用和参考备注
本项在[canvas-select](https://github.com/heylight/canvas-select)基础上做出改动实现，感谢该作者🙏。


npm run build
## 盒子模型
CSS盒子模型是网页布局的核心概念，每个HTML元素都被视为一个矩形盒子，由内容(content)、内边距(padding)、边框(border)和外边距(margin)四部分组成,以下是详细解析：

## 盒子模型组成

1. 内容区(Content)‌
通过width和height定义元素的实际内容尺寸，背景色默认覆盖此区域

``` html

<div class="w-64 h-32 bg-blue-200">内容区域</div>

```

2. 内边距(Padding)‌
控制内容与边框的间距，背景色会延伸至padding区域
Tailwind支持单边或统一设置，如p-4（四周）或px-2 py-3（水平/垂直）

``` html

<div class="p-4 border border-gray-300">内边距示例</div>

```

3. 边框(Border)‌
包含宽度、样式和颜色属性，Tailwind提供border-{size}、border-{color}等类

``` html

<div class="border-2 border-dashed border-red-500 p-4">虚线边框</div>

```

4. 外边距(Margin)‌
定义元素与其他元素的间距，支持负值（如-m-2）

``` html

<div class="m-8 bg-yellow-100">外边距示例</div>

```

5. 盒模型计算模式
‌标准模型‌：width/height仅定义内容区，总尺寸需加上padding和border
border-box模型：width/height包含padding和border，通过Tailwind的box-border启用

``` html

<div class="box-border w-64 p-4 border-2">总宽度包含padding和border</div>

```


- 结合Flexbox和Grid实现复杂布局示例

``` html
<div class="flex justify-center items-center h-screen">
  <div class="grid grid-cols-3 gap-4 w-full max-w-2xl">
    <div class="p-4 bg-white rounded-lg shadow-md">Box 1</div>
    <div class="p-4 bg-white rounded-lg shadow-md">Box 2</div>
    <div class="p-4 bg-white rounded-lg shadow-md">Box 3</div>
  </div>
</div>

```
- 高级特性
‌宽高比‌：使用aspect-video保持16:9比例
‌阴影与圆角‌：rounded-lg和shadow-xl快速美化

``` html
<div class="aspect-video bg-gray-200 rounded-xl shadow-lg"></div>

```
- 完整示例项目展示盒子模型综合应用：

``` html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tailwind盒子模型</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 p-8">
  <div class="max-w-4xl mx-auto space-y-6">
    <!-- 基础盒子 -->
    <div class="p-6 bg-white rounded-lg shadow-md border-l-4 border-blue-500">
      <h2 class="text-xl font-bold mb-2">标准盒子</h2>
      <p class="text-gray-600">内容区 + padding + border + margin</p>
    </div>

    <!-- Flex布局 -->
    <div class="flex flex-wrap gap-4">
      <div class="flex-1 min-w-[200px] p-4 bg-green-100 rounded border border-green-300">
        Flex子项1
      </div>
      <div class="flex-1 min-w-[200px] p-4 bg-green-100 rounded border border-green-300">
        Flex子项2
      </div>
    </div>

    <!-- 宽高比盒子 -->
    <div class="aspect-video bg-purple-200 rounded-xl overflow-hidden mt-6">
      <img src="https://picsum.photos/800/450" alt="示例图片" class="w-full h-full object-cover">
    </div>
  </div>
</body>
</html>

```


## 计算出当前月到前六个月，并把这六个月放到数组中

可以使用 moment.js 库来计算当前月份到前六个月份，并将这些月份放入一个数组中。下面是一个示例代码：

```jsx
import moment from 'moment';

const getPastMonths = () => {
  const pastMonths = [];
  const currentMonth = moment(); // 获取当前月份

  for (let i = 0; i < 6; i++) {
    const pastMonth = currentMonth.clone().subtract(i, 'months'); // 计算前 i 个月份
    pastMonths.push(pastMonth.format('YYYY-MM')); // 将月份格式化为 'YYYY-MM' 并放入数组
  }

  return pastMonths.reverse(); // 数组反转，使得数组中的月份按照从当前月到前六个月的顺序排列
}

// 使用示例
const monthsArray = getPastMonths();
console.log(monthsArray);
```

在这个代码中，我们使用 moment.js 库来获取当前月份，然后通过循环和 `subtract` 方法计算前六个月份，并使用 `format` 方法将月份格式化为 'YYYY-MM' 的形式，然后将其放入一个数组中。

最后，我们使用 `reverse` 方法将数组反转，以确保数组中的月份按照从当前月份到前六个月份的顺序排列。

这样，`monthsArray` 数组中就包含了当前月份到前六个月份的月份字符串，您可以在需要的地方使用这个数组来展示时间轴、生成 Tabs 组件等等。

## 用Array.from的方式进行遍历



```jsx
import moment from 'moment';

const getPastMonths = () => {
  const currentMonth = moment(); // 获取当前月份

  const pastMonths = Array.from({ length: 6 }, (_, i) => (
    currentMonth.clone().subtract(i, 'months').format('YYYY-MM')
  ));

  return pastMonths.reverse(); // 数组反转，使得数组中的月份按照从当前月到前六个月的顺序排列
}

// 使用示例
const monthsArray = getPastMonths();
console.log(monthsArray);
```

在这个代码中，我们使用 `Array.from` 方法生成一个长度为 6 的数组，并通过第二个参数的回调函数来计算数组中的每个元素。在回调函数中，我们使用 `currentMonth.clone().subtract(i, 'months').format('YYYY-MM')` 来计算前六个月份并将其格式化为 'YYYY-MM' 的形式，然后将其作为数组的元素。

最后，我们使用 `reverse` 方法将数组反转，以确保数组中的月份按照从当前月份到前六个月份的顺序排列。

这样，`monthsArray` 数组中就包含了当前月份到前六个月份的月份字符串，您可以在需要的地方使用这个数组来展示时间轴、生成 Tabs 组件等等。

## subtract详解

`subtract` 是 moment.js 库中的一个方法，用于从一个 moment 对象中减去指定的时间段。它接受两个参数：第一个参数是要减去的时间量，第二个参数是时间单位。

语法如下：

js

```js
moment().subtract(amount, unit);
```

其中，`amount` 是要减去的时间量，可以为正数或负数，表示要减去的时间的数量。`unit` 是时间单位，可以是以下字符串之一：

*   `'years'` 或 `'y'`：年
*   `'months'` 或 `'M'`：月
*   `'weeks'` 或 `'w'`：周
*   `'days'` 或 `'d'`：日
*   `'hours'` 或 `'h'`：小时
*   `'minutes'` 或 `'m'`：分钟
*   `'seconds'` 或 `'s'`：秒
*   `'milliseconds'` 或 `'ms'`：毫秒

例如，`moment().subtract(1, 'months')` 表示从当前时间减去一个月。`moment().subtract(2, 'weeks')` 表示从当前时间减去两周。`moment().subtract(3, 'days')` 表示从当前时间减去三天，依此类推。

`subtract` 方法返回一个新的 moment 对象，表示减去指定时间段后的时间。原始的 moment 对象不会被修改，而是返回一个新的 moment 对象，以保持 moment.js 的不可变性。


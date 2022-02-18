# JavaScript 的 ‘ = ‘ 知识

## === 的比较规则

#### 1. 如果Type(x)和Type(y)不同，返回false

#### 2. 如果Type(x)和Type(y)相同

1. 如果Type(x)是Undefined，返回true

2. 如果Type(x)是Null，返回true

3. 如果Type(x)是String，当且仅当x,y字符序列完全相同（长度相同，每个位置上的字符也相同）时返回true，否则返回false

4. 如果Type(x)是Boolean，如果x,y都是true或x,y都是false返回true，否则返回false

5. 如果Type(x)是Symbol，如果x,y是相同的Symbol值，返回true,否则返回false

6. 如果Type(x)是Number类型
   1. 如果x是NaN，返回false
   2. 如果y是NaN，返回false
   3. 如果x的数字值和y相等，返回true
   4. 如果x是+0，y是-0，返回true
   5. 如果x是-0，y是+0，返回true
   6. 其他返回false

> Type(x)：获取 x 的类型

##  == 比较规则

#### 1. 如果Type(x)和Type(y)相同，返回x===y的结果

#### 2. 如果Type(x)和Type(y)不同

1. 如果x是null，y是undefined，返回true

2. 如果x是undefined，y是null，返回true

3. 如果Type(x)是Number，Type(y)是String，返回 x==ToNumber(y) 的结果

4. 如果Type(x)是String，Type(y)是Number，返回 ToNumber(x)==y 的结果

5. 如果Type(x)是Boolean，返回 ToNumber(x)==y 的结果

6. 如果Type(y)是Boolean，返回 x==ToNumber(y) 的结果

7. 如果Type(x)是String或Number或Symbol中的一种并且Type(y)是Object，返回 x==ToPrimitive(y) 的结果

8. 如果Type(x)是Object并且Type(y)是String或Number或Symbol中的一种，返回 ToPrimitive(x)==y 的结果

9. 其他返回false

>ToNumber(x) : 将x转换为Number类型
>
>ToBoolean(x) : 将x转换为Boolean类型
>
>ToString(x) : 将x转换为String类型
>
>ToPrimitive(x) : 将x转换为原始值

## Object.is()

Object.is() 与 === 的比较规则几乎一致，区别在于以下比较规则

```js
//对于 NaN 的比较
Object.is( NaN , NaN )  // true
NaN === NaN //false
//对于 +0 与 -0 的比较
Object.is( +0 , -0 )  // false
+0 === -0 //true
```
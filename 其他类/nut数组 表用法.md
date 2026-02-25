


## <center>数组</center>

```squirrel title:声明一个数组
local iKeyList =[];
```

```squirrel title:更改数组的大小
iKeyList.resize(3);
iKeyList.resize(size,[fill]);
```

```squirrel title:设置数组中的元素
iKeyList[0] = 0;
iKeyList[1] = 15;
iKeyList[2] = -15;
```

```squirrel title:追加到数组末尾
iKeyList.append(666);
iKeyList.push(666);
```

```squirrel title:删除数组中的所有项目
iKeyList.clear();
```

```squirrel title:获取数组的长度
iKeyList.len();
```

```squirrel title:把另外一个数组加入到数组内
iKeyList.extend(array);
```

```squirrel title:删除数组最后面的一个值 并返回它
iKeyList.pop();
```

```squirrel title:返回一个较高索引的数组值
iKeyList.top();
```

```squirrel title:在数组的某个位置插入值
iKeyList.insert(idx,val);
```

```squirrel title:删除数组中某个位置的值
iKeyList.remove(idx);
```

```squirrel title:反向排序数组顺序
iKeyList.reverse();
```

```squirrel title:截取中间一段数组
//以新数组的形式返回数组的一部分。
//从开始到结束的副本(不包括)。
//如果开始为负，则计算索引长度+开始，如果结束为负，则计算索引长度+开始。
//如果结束被省略，结束等于数组长度。
iKeyList.slice(start,[end]);
```
## <center>表</center>
```squirrel title:
getroottable()["iceAreaRainCreatePos"] <- {};
getroottable()["iceAreaRainCreatePos"] = 
[
	[26,-30],[91,15],[-66,-5],[114,-39],[-37,-34],[-109,5],
	[26,20],[-20,4],[134,-12],[-92,-42],[-44,25],[-120,-23],
	[-23,-52],[62,-55],[55,1],[-10,-13],[84,-24]
];
```
```squirrel title:
//赋值给变量
local pos = ::iceAreaRainCreatePos[currentIndex];//取出数组
local x = pos[0];
local y = pos[1];
```
```squirrel title:
//得到总数
::iceAreaRainCreatePos.len();
```
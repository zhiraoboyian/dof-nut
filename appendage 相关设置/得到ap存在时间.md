```squirrel title:
local useTime = appendage.getTimer().Get();

//这里其实是得到的计时器 也可以有这样的操作
timer.Reset();//初始化
timer.Start(10000,0);//计时开始
local currentT = timer.Get();//得到时间
```
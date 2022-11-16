# 信号检测器

受金10数据的信号检测器启发，本人也想来尝试一下信号检测器的实现，看看mt4是否能做到这一部分，先初步构思一下，做一个裸K的信号检测器。



## 信号分类

open表示开盘价，close表示收盘价，max表示最高价，min表示最低价。

看跌吞没

```
open(t) < close(t) 
open(t+1) >= close(t)
close(t+1) <= open(t)
```

看涨吞没

```
open(t) > close(t)
open(t+1) <= close(t)
close(t+1) >= open(t)
```



启明之星

```
open(t) - close(t) >= m
|open(t+1) - close(t+1)| <= epsilon
close(t+2) - open(t+2) >= n 
```



黄昏之星

```
close(t) - open(t) >= m
|open(t+1) - close(t+1)| <= epsilon
close(t+2) - open(t+2) >= n 
```



看涨Pinbar

```
close(t) - min(t) >= max(t) - open(t)
```

看跌Pinbar

```
max(t) - open(t) >= close(t) - min(t)
```

乌云盖顶（看跌刺透）

```
open(t) < close(t)
open(t+1) > close(t+1)
close(t+1) < 1/2 * (open(t) + close(t))
```

看涨刺透

```
open(t) < close(t)
open(t+1) > close(t+1)
close(t+1) < 1/2*(open(t)+close(t))
```









## 图形化界面
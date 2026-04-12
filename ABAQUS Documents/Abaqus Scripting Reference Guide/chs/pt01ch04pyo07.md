# 4.7 Movie 对象





Movie 对象用于存储与电影文件关联的值和属性。创建时，Movie 对象被添加到 `session.movies` 仓库。

**访问**

```
import animation
session.movies[*name*]
```

### 4.7.1 Movie(...)

此方法从指定文件的内容创建 Movie 对象。

**路径**

```
session.Movie
```

**必需参数**

*name*

一个 String，指定电影的仓库名称。

*fileName*

一个 String，指定要从中读取电影的文件。必须指定文件扩展名并指示电影格式（`.avi`、`.mov`、`.mpeg` 或 `.wmv`）。

**可选参数**

*startFrame*

一个 Int，指定从此电影显示的第一帧。默认值为 0。

*endFrame*

一个 Int，指定从此电影显示的最后一帧。负数表示倒序：-1 是电影的最后一帧。默认值为 1。

*timelineStartFrame*

一个 Int，指定对应于 *startFrame* 的全局时间线帧号。值为 0 将指示要在视口中显示的第一帧。默认值为 0。

*timelineEndFrame*

一个 Int，指定对应于 *endFrame* 的全局时间线帧号。负数表示倒序：-1 表示要在视口中显示的最后一帧。默认值为 1。

*timelineStartTime*

一个 Float，指定对应于 *startFrame* 时间的全局时间线时间。默认值为 0.0。

*timelineEndTime*

SymbolicConstant END_FRAME_TIME 或一个 Float，指定对应于 *endFrame* 时间的全局时间线时间。SymbolicConstant END_FRAME_TIME 表示此电影中对应于 *endFrame* 的时间。默认值为 END_FRAME_TIME。

**返回值**

一个 Movie 对象。

**异常**

ValueError。

如果 *fileName* 不存在或无法读取：

```
ValueError: Unable to open movie file
```

如果 *fileName* 引用不支持的电影文件格式：

```
ValueError: Unsupported movie format
```

如果 *fileName* 的内容损坏或无法解码：

```
ValueError: Unable to decode movie file
```

### 4.7.2 setValues(...)

此方法修改 Movie 对象。

**必需参数**

无。

**可选参数**

*startFrame*

一个 Int，指定从此电影显示的第一帧。默认值为 0。

*endFrame*

一个 Int，指定从此电影显示的最后一帧。负数表示倒序：-1 是电影的最后一帧。默认值为 1。

*timelineStartFrame*

一个 Int，指定对应于 *startFrame* 的全局时间线帧号。值为 0 将指示要在视口中显示的第一帧。默认值为 0。

*timelineEndFrame*

一个 Int，指定对应于 *endFrame* 的全局时间线帧号。负数表示倒序：-1 表示要在视口中显示的最后一帧。默认值为 1。

*timelineStartTime*

一个 Float，指定对应于 *startFrame* 时间的全局时间线时间。默认值为 0.0。

*timelineEndTime*

SymbolicConstant END_FRAME_TIME 或一个 Float，指定对应于 *endFrame* 时间的全局时间线时间。SymbolicConstant END_FRAME_TIME 表示此电影中对应于 *endFrame* 的时间。默认值为 END_FRAME_TIME。

**返回值**

无

**异常**

RangeError。

如果 *startFrame*、*endFrame*、*timelineStartFrame*、*timelineEndFrame*、*timelineStartTime* 或 *timelineEndTime* 超出其各自的有效范围。

```
RangeError: startFrame must be an Integer in the range: 0 to numFrames-1 
```

### 4.7.3 成员

Movie 对象具有与 [Movie](pt01ch04pyo07.md#ker-movie-movie-pyc) 方法参数相同名称和描述的成员。

此外，Movie 对象可以具有以下成员：

*width*

一个 Int，指定电影的宽度（以像素为单位）。

*height*

一个 Int，指定电影的高度（以像素为单位）。

*numFrames*

一个 Int，指定电影文件上的总帧数。

*duration*

一个 Float，指定电影的持续时间（以秒为单位）。

*memory*

一个 Int，指定所选电影帧所占用的内存。





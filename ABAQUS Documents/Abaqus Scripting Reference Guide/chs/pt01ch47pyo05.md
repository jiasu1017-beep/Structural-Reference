# 47.5 Image 对象





Image 对象用于存储与光栅文件关联的颜色值和属性。创建时，Image 对象会被添加到 `session.images` 存储库。

**访问**

```
session.images[*name*]
```

### 47.5.1 Image(...)

此方法从指定文件的内容创建 Image 对象。

**路径**

```
session.Image
```

**必要参数**

*name*

String，指定图像的存储库名称。

*fileName*

String，指定要从中读取图像的文件。必须指定文件扩展名并指示图像格式（`.bmp`、`.gif`、`.jpg`、`.jpeg`、`.ico`、`.pcx`、`.png`、`.rgb`、`.tga`、`.tif` 或 `.xpm`）。

**可选参数**

无。

**返回值**

Image 对象。

**异常**

ValueError。

如果 *fileName* 不存在或无法读取：

```
ValueError: Unable to open image file
```

如果 *fileName* 引用不支持的图像文件格式：

```
ValueError: Unsupported image format
```

如果 *fileName* 的内容损坏或无法解码：

```
ValueError: Unable to decode image file
```

### 47.5.2 ImageFromMovie(...)

此方法从现有 [Movie](pt01ch04pyo07.md) 对象的给定帧创建 Image 对象。

**必要参数**

*name*

String，指定图像的存储库名称。

*movieName*

String，指定要从中提取图像的电影名称。电影必须存在于 session.movies 存储库中。

*frame*

Int，指定定义要提取的图像的电影帧编号。

*time*

Float，指定定义要提取的图像的电影时间。

**可选参数**

无。

**返回值**

Image 对象。

**异常**

ValueError。

TypeError。

如果 *movieName* 不存在：

```
ValueError: There is no movie object with this name: 'movieName'
```

如果 *frame* 引用不存在的帧：

```
ValueError: Could not load frame n from movie: 'movieName'
```

如果 *time* 引用不存在的帧：

```
ValueError: Could not load frame at time 't' from movie: 'movieName'
```

如果在同一命令中同时给出了 *time* 和 *frame*：

```
TypeError: keyword error on time
```

### 47.5.3 成员

Image 对象的成员与 [Image](pt01ch47pyo05.md#ker-image-image-pyc) 方法的参数具有相同的名称和描述。



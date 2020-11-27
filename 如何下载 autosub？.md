# 如何下载 autosub？

python的autosub库能够自动生成字幕文件，是日常看剧或者翻译的必备神器。那么如何安装 autosub 包呢？

首先必要的条件如下：

- 安装 python3.6 以上



## 1. 安装 aotosub 库

接下来先安装必要的库，最好直接去该项目的GitHub主页上下载，地址是：https://github.com/agermanidis/autosub，选择 `code` 并选择 `Download ZIP` 下载该压缩文件。接下来把它压缩出来，并复制所在的地址，如 `C:\fanzhuan\Downloads\autosub-master` ，打开命令行（快捷键WIN+R，输入cmd回车即可），输入

```
cd C:\fanzhuan\Downloads\autosub-master
```

转到文件所在的目录下，然后在运行下列代码下载该安装包

```
python setup.py install
```

如果没有发生错误，该下载便完成了。

我们继续打开命令行，输入

```
autosub -h
```

如果没有发生错误说明安装完成。



## 2. 安装 ffmpeg

这个安装也非常简单，不过主要下载后好记得添加环境变量。

下载地址为：https://www.ffmpeg.org/download.html

如果安装好了并添加了环境变量，可以打开命令行测试一下

```
ffmpeg -h
```

如果没有发生错误，那么安装便完成了。那么恭喜你可以继续使用了。



## 3. 可能发生的错误

我在本次使用中出现两处错误：

1. 发生如下错误，该原因是 google-auth 包版本冲突了，你需要升级你的库。

```
raise VersionConflict(dist, req).with_context(dependent_req)
pkg_resources.ContextualVersionConflict: (google-auth 1.20.0 (c:\users\13631\appdata\local\programs\python\python38\lib\site-packages), Requirement.parse('google-auth<2.0dev,>=1.21.1'), {'google-api-core'})
```

我们通过重新安装即可，命令行输入

```
pip install google-auth==1.22.0
```



2. 出现 `ffmpeg: Executable not found on machine.`

这是由于autosub的`__init__.py` 的设置问题，需要修改该文件，然后再重新下载。我们可以打开刚刚下载的那个叫 `autosub-master` 的文件包，找到 `__init__.py` 文件，讲下列语句

```
if not which("ffmpeg"):
```

修改为

```
if not which("ffmpeg.exe"):
```

即可。

然后重新安装一下这个包，步骤与一步骤相同。
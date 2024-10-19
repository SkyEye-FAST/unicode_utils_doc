# 安装

## 从PyPI安装

Unifont Utils目前仅支持Python 3.9及以上版本。请参见[PyPI上的项目页面](https://pypi.org/project/unifont_utils/)。

请使用下面的命令从PyPI安装Unifont Utils：

``` shell
pip install unifont_utils
```

!!! tips
    如果`pip`命令无效，请尝试使用`pip3`或在命令前加上`python3 -m`。

### 更新

请使用下面的命令更新Unifont Utils：

``` shell
pip install --upgrade Pillow
```

## 从源代码安装

如果需要从源代码安装，请先[安装Poetry](https://python-poetry.org/docs/#installation)。

从GitHub上将项目克隆到本地：

``` shell
git clone https://github.com/SkyEye-FAST/unifont_utils.git
```

进入项目目录，然后使用下面的命令安装：

``` shell
poetry install
```

## 从`.whl`文件安装

如果无法直接在终端里从PyPI安装，可以从PyPI或[GitHub Releases](https://github.com/SkyEye-FAST/unifont_utils/releases)下载`.whl`文件。

此外，每次提交后，项目都会借助[GitHub Actions](https://github.com/SkyEye-FAST/unifont_utils/actions)自动构建开发状态的项目，可以下载此处构建的包来测试最新版本。

获得`.whl`文件后，请使用下面的命令安装：

``` shell
pip install unifont_utils-<version>-py3-none-any.whl
```

其中`<version>`取决于下载的`.whl`文件版本号。

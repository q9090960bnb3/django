# Introduction

## 安装python

```sh
# 安装PPA需要的软件源
apt install software-properties-common -y
# 添加名为deadsnake的PPA源
add-apt-repository ppa:deadsnakes/ppa
# 安装指定python 版本
apt install python3.10
```

## 创建隔离环境

### 自带方式

https://docs.python.org/3/tutorial/venv.html

```sh
# 安装 python3.8-env 隔离环境工具
apt install python3.8-env
# 创建环境
python -m venv tutorial-env
# 使用 tutorial-env 隔离环境
source tutorial-env/bin/activate
# 退出隔离环境
deactivate
```

### poetry

https://notes.zhengxinonly.com/environment/use-poetry.html

- 安装

```sh
# 安装
pip install poetry
```

- 创建项目

方式一

```sh
poetry new poetry-demo
```

方式二

```sh
mkdir poetry-demo
poetry init
```

- 创建环境

```sh
poetry env use python3
```

- 激活虚拟环境

```sh

poetry shell
```

- 查看设定

```sh
poetry config --list
```

- 删除虚拟环境

```sh
poetry env remove python3
```

- 将虚拟环境放入项目目录

```sh
poetry config virtualenvs.in-project true
# 再次使用创建环境命令后环境就在项目根目录了
```

- 安装模块

```sh
poetry add
```

- 更新poetry.lock

当你自行修改了 pyproject.toml 内容，比如变更特定模块的版本（这是有可能的，尤其在手动处理版本冲突的时候），此时 poetry.lock 的内容与 pyproject.toml 出现了脱钩，必须让它依照新的 pyproject.toml 内容更新、同步，使用指令

```sh
poetry lock
```

- 新增模块至 dev-dependencies

有些模块，比如 pytest 、 black 等等，只会在开发环境中使用，产品的部署环境并不需要。

Poetry 允许你区分这两者，将上述的模块安装至 dev-dependencies 区块，方便让你轻松建立一份「不包含」 dev-dependencies 开发模块的安装清单。

在此以 Black 为例，安装方式如下：

```sh
poetry add black --group dev
```

- 更新模块

```sh
poetry update
# 指定更新
poetry update requests toml
```

- 列出模块清单

```sh
poetry show
poetry show --tree
poetry show celery --tree
```

- 移除模块

```sh
poetry remove flask
```
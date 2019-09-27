# shell 常规用法备忘
## 变量赋值
```shell
NAME="hello world"
echo $NAME
```

## 获取执行文件所在绝对路径
```shell
DIRNAME = $(cd "$(dirname "$0")"; pwd)
echo $DIRNAME
```

## 文件末尾追加字段并保存
```shell
echo 'registry=https://npm-registry.yy.com' >> ~/.npmrc
```
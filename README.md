# 受约束工况组合的覆盖缺口与不可达证明

本项目保存虚构台架测量表及Python读取工具。当前工具加载文件并检查输入，不执行统计检验、求解、配准或分析。所有仪器、试件、对象与人工标签均为合成。

## 字段与单位

factors的变量域均有穷。forbidden项是不可同时满足的部分赋值；implications为if部分赋值则then部分赋值。completed每行必须提供所有因素，status=complete才是完成试次。

material-index.json记录全部输入内容哈希；fixtures保存原始资料与配置，计算输出可放.workspace-output，原始资料不应被覆盖。

## 运行已有读取器

Python 3.11以上，标准库即可，不需安装第三方依赖。

    python -m src.coverage_reader fixtures/factors.json
    python -m compileall -q src tests
    python -m unittest discover -s tests -v

## 固定容器

    docker build -t scenario-coverage:local .
    docker run --rm scenario-coverage:local

容器镜像以完整digest固定，默认仅检查输入契约；实现新增分析功能所需依赖由开发者明确登记。

# 社区公共服务可达性

本项目使用 Python 3.11 及以上版本，仅依赖标准库，无需安装第三方包。数据文件均为本地合成记录，不含真实个人或机构资料。

network 校验有向网络并按出行方式求最短路；catchments 形成可达服务关系；supply 处理共享供给池与需求竞争；equity 汇总服务缺口；analysis_runs 保存输入修订和分析。

共享供给池只计算一次容量。浮动可达性指数不是服务概率，分数规划量不是实际人员派遣。路由成本固定，有向路径、无障碍限制和实际供给分开解释。

在项目根目录运行完整测试：

```sh
python3 -m unittest discover -s tests -v
```

编译检查：

```sh
python3 -m compileall -q .
```

实际演示：

```sh
python3 accessibility.py demo --fixture fixtures/community.json
```

演示在临时目录内建立本地状态，结束后自动清理。测试、编译与演示在依赖已准备的环境内均不下载数据或软件。输入错误以非零退出码及错误对象报告。更多子命令可通过对应入口的 --help 查看。

容器环境可执行 `docker build -t local-analysis .`，再运行 `docker run --rm --network none local-analysis`。镜像固定基础内容摘要，构建后运行只访问本地文件。完整测试与演示也可直接使用已有 Python 环境。

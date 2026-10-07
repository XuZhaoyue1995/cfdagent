# 经典案例与验证资料入口

需要学习配置、检查安装、验证改动或寻找物理对照时查阅。以下是上游官方资料索引，2026-09-22 核对可检索内容；**不代表 CFDAgent 已在本地运行或验收这些案例**，也不限制其他求解器和新算例。

| 官方入口 | 可查的案例或内容 | 使用时留意 |
| --- | --- | --- |
| [OpenFOAM 后向台阶，v2212](https://doc.openfoam.com/2212/examples/verification-validation/turbulent/backward-facing-step/) | 湍流分离、再附与速度/壁面量的实验对照 | 记录发行分支、模型和近壁设置，不能只匹配 Re |
| [SU2 教程集](https://su2code.github.io/tutorials/home/) | 层流平板、圆柱、超声速楔、ONERA M6 等 | 按方程、可压缩性和教程版本取配置；示例运行完成不等于完成验证 |
| [FDS 官方手册](https://pages.nist.gov/fds/manuals.html) | 分开的 Verification Guide 与 Validation Guide | 选与目标火灾/烟热输运现象相符的数据集，读取实验条件和不确定度 |
| [MFiX V&V 手册第三版](https://mfix.netl.doe.gov/doc/vvuq-manual/main/html/index.html) | MMS、Poiseuille/Couette、颗粒沉降、DEM/PIC 测试 | 不同模型分开验收；制造解检验方程实现，不能替代实验验证 |
| [DualSPHysics 官方 Testcases](https://github.com/DualSPHysics/DualSPHysics/wiki/7.-Testcases) | 溃坝、晃荡、造波及配套参考数据说明 | 分清二维/三维案例、边界处理与测点位置，按安装版本核对文件名 |
| [Basilisk 官方测试目录](https://www.basilisk.fr/src/test/README) | VOF 平流、毛细波、静滴、嵌入边界等测试 | 自适应准则、界面量和误差范数取对应测试定义；圆柱 Couette 不等于平板 Couette |
| [Nek5000 官方教程](https://nek5000.github.io/NekDoc/tutorials.html) | 充分发展层流、周期丘陵、共轭传热等 | 单元数与谱元阶数都影响分辨率；不直接当作 nekRS 已验收证据 |
| [PyFR v2.1 官方示例](https://pyfr.readthedocs.io/en/v2.1/examples.html) | Euler 涡、Couette、不可压圆柱、Taylor–Green 等 | 高阶格式与后端版本需记录；这些小示例不适合直接作性能/扩展性研究 |

其他求解器依 [solver-selection.md](solver-selection.md) 的官方入口查找；索引空缺不是该求解器能力不足。PyIB 的项目证据来自对应仓库和实际运行记录，不因旗舰地位获得自动验证结论。

## 把参考变成本项目证据

只在确有用途时引入案例。记录来源 URL/DOI、版本或提交、案例名、方程与参数范围、边界/几何假设、参考量定义、单位、参考数据文件及不确定度。引用图表数字时保存原图/表编号和提取方式；不要凭图像印象写成精确实验值。

区分：官方示例、官方验证数据、本地复现、当前工况验证。记录实际改动、运行标识、目标量误差、结果文件与适用范围。已复现案例可以复用其证据，但新版本、模型或参数变化需判断是否仍被覆盖。

优先使用有误差定义的解析/制造解检查实现；与实验比较时分开考虑输入、数值与模型误差。跨求解器对照能暴露差异，不能自动证明共同结果正确。具体如何判断和安排补算见 [result-validation.md](result-validation.md)。

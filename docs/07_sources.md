# 07 来源、哈希与版本关系

> 本文件回答：每个数字从哪来、原文件是什么、为什么有些文件没上传。
> 所有哈希为 SHA-256（小写，前 64 位全串）。原项目根目录为内部工作区（不随仓库发布）；下表中的相对路径均相对该目录。

---

## 1 一手来源

### 1.1 文献

| 项 | 内容 |
|---|---|
| 文件 | `aoc_group_meeting_20261020/sources/Adaptive_Optimization_Charging_Strategy_for_LCC_Resonant_Capacitor_Charging_Power_Supply.pdf` |
| 大小 | 4,297,589 B |
| SHA-256 | `547dcff2f8430b8c135c7c626535bfa8a4a74d3b8df7c0a5a5ced57aa20fff29` |
| 用途 | 文献精读、公式、实验参数、页码定位 |
| 公开状态 | **不随仓库分发**（IEEE 版权）；引用 DOI |

### 1.2 项目最终轨迹与报告

| 文件（相对项目根） | 大小 | SHA-256 | 用途 |
|---|---:|---|---|
| `MATLAB_PRJ/three_phase/aoc_feasibility_20261017/aoc_reoptimization_20261020/AOC_NEW_OPTIMUM_REPORT.md` | 7,737 | `29106caa265d9cc383b3c4716521e69cec293262c6c4a44d0f7ff66e66d7430b` | 新最优方案、20 段表、约束与搜索 |
| `.../aoc_reoptimization_20261020/LOCAL_254V_REVISION_REPORT.md` | 4,120 | `6b495010b86e5d35841edcce3a3c649f406cc1fb2137d1364f86a64363833c31` | 254 V 修订、41 点、59 节点 |
| `.../aoc_reoptimization_20261020/data/local_254V_revision_20261020/revision_summary.json` | 2,834 | `41832c21677ae312024ff18aa075b4758830ed5cd55271896d69d96b38c2f2b9` | 权威数值（2.089438 ms 等） |
| `.../aoc_reoptimization_20261020/data/local_254V_revision_20261020/aoc_smooth254_59_nodes.csv` | 6,678 | `03b017c7943e84d590317ba291c94fcb1e7486589f2a9d86842fc0630ea4ff88` | **最终 59 节点表** |
| `MATLAB_PRJ/three_phase/aoc_feasibility_20261017/next_round_physical_validation/FULL_CHARGE_REPORT.md` | 10,789 | `2316e29b49537f2a1664206111784c6caa12210c7a882ff0a956925e085122a5` | M2 三条轨迹、末端 7 频点、停充 |
| `.../next_round_physical_validation/ZVS_VALIDATION_REPORT.md` | 14,142 | `68d5c325636405b91f682ea817f30fcd6fd8dd1f2164861828c8bce41dba2199` | 换流/残压诊断 |

### 1.3 20 点验证与动态

| 文件（相对项目根或上一归档） | 大小 | SHA-256 | 用途 |
|---|---:|---|---|
| `model_comparison_HOGA_EDF_FHA/charging_trajectory_AOC_10point_validation/reports/AOC_20point_accuracy_report.md` | 9,893 | `9199daefb171ada34882d8c40f3fdbeacd7e65d7b1ac4541a62a148b3e5700fd`（归档版 10,227 B，内容同源） | 20 点结果、准静态边界 |
| `.../reports/AOC_control_retrofit.md` | 3,115 | `3d9fe636bf507a52fa483f5694987975881b44b73b3f7ab0a335fa2b2137f2a8`（归档版 3,543 B） | 查表、锁存、t800=2.151012/2.153487 |
| `.../data/aoc/accuracy_summary.csv` | 595 | `4b7020ba673ba1bff0b4e02c7e6e5dd5ce77214bc827f0dae1789715d8b6792a` | MAPE/MAE 汇总 |

> 归档版比原报告多了一段“归档说明”，哈希不同；数值内容一致。本包使用归档版的数字，并在 `data/` 中保留 CSV。

### 1.4 文献汇报定稿

| 文件（相对项目根） | 大小 | SHA-256 | 用途 |
|---|---:|---|---|
| `aoc_group_meeting_20261020/release-final/AOC_组会逐页讲稿.md` | 11,632 | `c4c1c7ef45ec95be4d91417f9a7ca5000fc489195bf2713b08fc9c10547ec983` | 7 页讲稿、A 点/式 (20) 解释 |
| `.../release-final/AOC_导师可能提问及回答.md` | 9,335 | `3721bd58fedd8f69f32a1f02c566ce6353d5e66a4822babae3b80a1b2dd3b766` | 12.35%/10.99%、热仿真、ZVS 边界 |
| `artifacts/strategy_review_20261020/充电策略重选评估.md` | 15,593 | `5b620c5f6fd96fb66272a7c6a4146af8f6275bafcffc9ad20995a9974deca99a` | 21 节点 M2 三策略、14/21 节点取下限、旧表 2.572428 |

---

## 2 数字到来源的映射

| 数字 | 来源 | 备注 |
|---|---|---|
| 2174 W、45 V、720 V、8.13 mF、105 A、1.63 μH、6.22 μF、n=16 | Qin 2023 Table III、§V | PDF p.10–11 |
| 61–67 kHz、1.82 s、1.62 s、12.35% | Qin 2023 §V-B、Fig.23 | PDF p.11–12 |
| 42.3/53 °C、损耗×4 | Qin 2023 §V-C、Fig.25 | PDF p.12 |
| 720 V 末端 ZVS | Qin 2023 §V-D、Fig.27 | PDF p.13 |
| 59 节点、241.5905–299.2573 kHz、13.99995 A、1.43999 A、1.85547→0.79996 A | `aoc_smooth254_59_nodes.csv` | 本包 `data/aoc_59_nodes.csv` |
| 2.089438 ms | `revision_summary.json` → `smooth_59node_time20to800_ms` | 准静态 20→800 V |
| 2.153487 ms | `AOC_20point_accuracy_report.md`、`AOC_control_retrofit.md` | M1 动态 |
| 2.151012 ms | `AOC_control_retrofit.md` | M0 理想 |
| 2.596206 ms | `AOC_20point_accuracy_report.md` | M1 旧 21 节点 |
| 2.544446 ms | `AOC_NEW_OPTIMUM_REPORT.md` | 旧窗口准静态 |
| 2.184381 ms、14.151% | 同上 | 20 段实施表 |
| 2.098458 ms、17.528% | 同上 / `revision_summary.json` | 逐节点候选 |
| 2.572428 / 2.940227 / 2.687160 ms | `FULL_CHARGE_REPORT.md` | M2 三策略 |
| 14.279921 / 14.308856 / 14.309823 A | 同上 | M2 相峰值 |
| 10.202091 / 10.537157 / 10.603515 mJ | 同上 | M2 直接耗散（4 ms） |
| 12.509% / 3.180% | 同上 + `strategy_review` 复算 | M2 旧表 vs 定频 |
| 800 V 末端 7 频点 | `FULL_CHARGE_REPORT.md` | 280/285/290/295/297/299/300 kHz |
| 20 点 MAPE/MAE | `accuracy_summary.csv`、`accuracy_10points.csv` | E3 |
| 41 点、1.95 V、13.999485 A、9.853760 A | `LOCAL_254V_REVISION_REPORT.md` | 215–293 V |
| 254 V 三个版本 | `revision_summary.json`、`LOCAL_254V_REVISION_REPORT.md` | 251.0643/243.8943/244.2735 kHz |

---

## 3 本包如何生成

1. 读取上述一手文件（Markdown/CSV/JSON/PDF 文本抽取）；
2. 用 Python 从 59 节点 CSV 重算统计（节点数、频率 min/max、`Ipk` max、`Icomm` min、`Io` min/max）；
3. 用 Python 复算百分比（17.053%、17.882%、17.528%、14.151%、12.7359%）；
4. 复制最终 CSV 与项目自生成图到 `data/`、`figures/`；
5. 用 `tools/build_site.py` 生成 `index.html`；
6. 用 `SHA256SUMS.txt` 固定文件哈希。

**没有做的事**：没有运行 MATLAB/Simulink/Maxwell，没有重跑 59 节点 M2 全程，没有改原模型，没有新增实验。

---

## 4 为什么有些文件没上传

| 文件/目录 | 原因 |
|---|---|
| 原论文 PDF | IEEE 版权，公开仓库不分发 |
| 论文原图（Fig.2/4/5/10–14/23/25/27 截图） | 同上；本包只用文字与项目自生成图 |
| `*.slx`（`AOC_charge.slx`、`ideal_three_phase_LCC*.slx`） | 体积、模型依赖与写作无直接关系；需要时回原工作区 |
| `*.mat` 全波形、`runtime/` 缓存 | 体积大；本包只保留可读 CSV |
| PPT v1–v5、`release/` 旧包 | 非最终版；最终文字结论已提炼 |
| 论文合排稿 `.docx` | 属于论文本体；本包只给改写骨架 |
| 内部绝对路径、协作记录、账号信息 | 公开仓库不保留 |

---

## 5 版本关系（与最终表的距离）

```
2026-10-17  21 节点 280–299 kHz 表（历史对照）
              ├─ 14/21 节点取 280 kHz 下限
              ├─ M2 全程 2.572428 ms、14.279921 A、4 次启动失败
              └─ 被 59 节点表取代

2026-10-20  扩域 + 局部加密
              ├─ 20 段实施表 2.184381 ms（中间保守参考）
              ├─ 逐节点候选 2.098458 ms（254 V 有尖峰）
              └─ 254 V 修订 → 59 节点 2.089438 ms（最终）

2026-10-24  59 节点表动态 + 20 点验证
              ├─ M1 t800 2.153487 ms
              ├─ 旧 21 节点同模型 2.596206 ms（−17.05%）
              └─ H49 Io MAPE 0.00566%（20/20）
```

> 每一行都只在自己那一层成立；不要跨行构造“总提升”。

---

## 6 复现入口（原工作区）

| 目的 | 入口 |
|---|---|
| 重算 59 节点统计 | `data/aoc_59_nodes.csv`（本包）或原 `aoc_smooth254_59_nodes.csv` |
| 重跑 59 节点 M1 动态 | `model_comparison_HOGA_EDF_FHA/charging_trajectory_AOC_10point_validation/models/AOC_charge.slx` |
| 重跑 20 点 | 同上 `scripts/`（需要原工作区数据与 MATLAB） |
| 重跑 M2 全程 | `aoc_feasibility_20261017/next_round_physical_validation/`（旧 21 节点） |
| 看 254 V 修订 | `aoc_reoptimization_20261020/scripts/validate254SmoothPath.m` 等 |
| 看文献汇报 | `aoc_group_meeting_20261020/release-final/` |

> 本包不保证这些脚本在另一台机器上可直接运行；MATLAB 版本、路径、数据依赖见原项目交接文档。

---

## 7 引用与许可

- 原论文：© 2023 IEEE。本仓库不复制原文、不复制原图；引用请用 DOI。
- 本包原创整理文字、表、项目自生成图：CC BY 4.0（见 `LICENSE_DOCS.md`）。
- 项目 CSV 数据：按原项目约定；本包只做公开归档。
- 代码/脚本：MIT（见 `LICENSE`）。

---

*本文件是来源账本，不是新研究。最后更新：2026-10-25。*

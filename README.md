# RetailScope：零售数据仓库与 Tableau 经营看板

> 从明细销售数据建到星型数仓，再用 Tableau 出一套可解释的经营决策看板。

## 项目定位

面向零售经营分析场景：先把 11 万行销售明细建模成星型数仓（事实表 + 维度表），
再用统一的指标口径产出 14 个 KPI 与 4 张多图看板，回答"卖得怎么样、问题出在哪、下一步该做什么"。

## 核心能力

- **星型数仓建模** —— 113,306 行销售事实表 + 维度表，SQLite 与 MySQL 双份 DDL 保持同构。
- **14 个 KPI 与统一指标口径** —— 口径写在 `docs/metric_dictionary.md`，SQL 与 Tableau 两侧共用同一份定义，避免"同名不同义"。
- **4 张多图 Tableau 看板** —— 含专业工作簿、PDF 与 HTML 预览，不依赖 Tableau 也能查看结论。
- **数据质量校验** —— 9 项检查覆盖主键唯一性、维度完整性、金额非负等。
- **自动化测试** —— 7 项测试全部通过。

## 项目内容导航

| 路径 | 内容 |
|---|---|
| `01_sql_dwh_tableau_dashboard/docs/database_design.md` | 星型模型与 ER 设计 |
| `01_sql_dwh_tableau_dashboard/docs/metric_dictionary.md` | 14 个 KPI 的口径定义 |
| `01_sql_dwh_tableau_dashboard/sql/schema_*.sql` | 建表 DDL（SQLite / MySQL 两版） |
| `01_sql_dwh_tableau_dashboard/sql/metrics_*.sql` | 指标计算 SQL |
| `01_sql_dwh_tableau_dashboard/src/build_dwh.py` | 数仓构建 |
| `01_sql_dwh_tableau_dashboard/src/validate_dwh.py` | 数据质量校验 |
| `01_sql_dwh_tableau_dashboard/src/build_tableau_*.py` | Tableau 工作簿与看板生成 |

## 环境安装

```powershell
pip install -r 01_sql_dwh_tableau_dashboard/requirements.txt
# 需要 Tableau 相关依赖时另装： -r 01_sql_dwh_tableau_dashboard/requirements-tableau.txt
```

## 快速开始

```powershell
.\01_sql_dwh_tableau_dashboard\run.ps1
```

## 项目结构

```
01_sql_dwh_tableau_dashboard/
├── docs/        数仓设计与指标口径
├── sql/         建表与指标 SQL（SQLite / MySQL）
├── src/         数仓构建 / 校验 / 看板生成 / 数据导出
├── tests/       自动化测试
└── run.ps1      一键运行
```

## 说明与边界

销售明细为**固定随机种子生成的模拟数据**，用于演示建模与看板链路；
指标口径与建模方法可迁移到真实业务，但结论本身不具备业务参考价值。

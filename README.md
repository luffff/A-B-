[README.md](https://github.com/user-attachments/files/29582333/README.md)
# A/B 测试分析项目

## 功能点击率提升效果评估

本项目基于 12 万条用户 A/B 实验数据，对产品新版功能的点击率（CTR）提升效果进行端到端统计分析，包含数据清洗、探索性分析、统计推断、效应量评估及分层验证。

---

## 数据集

| 项目 | 说明 |
|------|------|
| 数据量 | 120,000 条 |
| 分组 | Control（对照）60,000 条 / Test（实验）60,000 条 |
| 字段 | user_id, group, views（页面浏览数）, clicks（点击次数） |
| 类型 | 模拟网站行为日志数据 |

---

## 分析流程

1. **数据清洗与探索性分析** — 校验分组均衡性、分析分布特征
2. **整体点击率对比** — 计算 Control 与 Test 组的整体 CTR 及提升幅度
3. **统计假设检验** — 双比例 Z 检验、Welch T 检验、Mann-Whitney U 检验交叉验证
4. **置信区间估计** — 计算 CTR 差值的 95% 置信区间
5. **效应量与统计功效** — Cohen's h、Cohen's d、事后功效分析
6. **分层分析** — 按用户活跃度（低/中/高频）验证效果一致性
7. **结论与业务建议**

---

## 核心结论

| 指标 | Control | Test | 差异 |
|------|---------|------|------|
| 整体点击率（CTR） | 3.47% | 3.85% | **+11.05% 相对提升** |
| 总点击量 | 10,303 | 11,620 | +1,317 次额外点击 |
| 统计显著性 | — | — | 四种检验均显著（p < 0.001） |
| 统计功效 | — | — | 94.24%（远超 80% 阈值） |

### 统计检验结果

| 方法 | 统计量 | p 值 | 结论 |
|------|--------|------|------|
| 双比例 Z 检验 | Z = 7.89 | 2.94e-15 | 高度显著 |
| Welch T 检验 | T = 8.05 | 4.26e-16 | 高度显著 |
| Mann-Whitney U 检验 | U = 1.83e9 | 1.68e-13 | 高度显著 |
| CTR 差值 95% CI | [0.29%, 0.48%] | 不含 0 | 统计显著 |

### 分层分析

| 用户分层 | Control CTR | Test CTR | 相对提升 |
|----------|-------------|----------|----------|
| 低频（1-2 次浏览） | 2.06% | 2.69% | +30.6%（p<0.001） |
| 中频（3-5 次浏览） | 3.44% | 3.94% | +14.5%（p<0.001） |
| 高频（6+ 次浏览） | 3.73% | 4.01% | +7.5%（p<0.001） |

---

## 业务建议

1. **全量上线** — 新版功能显著提升 CTR，建议发布至所有用户
2. **持续监测** — 追踪下游转化、留存等长期指标
3. **分段优化** — 效应量偏小，可针对特定用户群做进一步优化
4. **延长实验** — 评估新奇效应（Novelty Effect）是否消退

---

## 技术栈

| 工具 | 用途 |
|------|------|
| Python | 核心分析语言 |
| Pandas / NumPy | 数据处理与计算 |
| SciPy / StatsModels | 统计检验与推断 |
| Matplotlib / Seaborn | 数据可视化 |
| Jupyter Notebook | 交互式分析环境 |

## 统计方法

- 双比例 Z 检验（Two-Proportion Z-Test）
- Welch T 检验（Welch's T-Test）
- Mann-Whitney U 非参数检验
- Cohen's h & Cohen's d 效应量
- 95% 置信区间
- 事后功效分析（Post-hoc Power Analysis）
- 分层分析（Segmentation Analysis）

---

## 文件说明

| 文件 | 说明 |
|------|------|
| ab_test_results_aggregated_views_clicks_2.csv | 原始实验数据 |
| ab_test_analysis.ipynb | 完整分析 Notebook |
| AB测试分析作品集.docx | 分析报告（作品集用） |
| eda_distributions.png | 浏览量与点击量分布图 |
| ctr_overview.png | CTR 对比图 |
| per_user_ctr_dist.png | 每用户点击率分布图 |
| segmentation_analysis.png | 分层分析对比图 |

---

## 运行方式

`ash
# 安装依赖
pip install pandas numpy scipy statsmodels matplotlib seaborn jupyter

# 启动 Notebook
jupyter notebook ab_test_analysis.ipynb
`

---

## 作者

数据分析项目作品集

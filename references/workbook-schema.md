---
AIGC:
  ContentProducer: '001191110102MAD55U9H0F10002'
  ContentPropagator: '001191110102MAD55U9H0F10002'
  Label: '1'
  ProduceID: 'e9204495-4d5e-4b6e-a5dd-d9e69607f769'
  PropagateID: 'e9204495-4d5e-4b6e-a5dd-d9e69607f769'
  ReservedCode1: '0ec4c3ea-5429-4302-a9d5-8115b71a1716'
  ReservedCode2: '0ec4c3ea-5429-4302-a9d5-8115b71a1716'
---

# Workbook Schema

## `测试条件.xlsx`

Sheets and headers:

1. `正交法测试场景`: `条件1`, `条件2`, `条件3`
2. `边界值测试场景`: `参数名称`, `参数类型`, `有效值`, `最小值`, `最大值`, `小于最小值`, `大于最大值`, `特殊值`
3. `等价类测试场景`: `参数名称`, `参数类型`, `有效等价类1`, `有效等价类2`, `有效等价类3`, `无效等价类1`, `无效等价类2`, `无效等价类3`, `说明`
4. `场景法测试场景`: `场景ID`, `场景名称`, `前置条件`, `触发条件`, `场景步骤`, `数据依赖`, `预期结果`, `备注说明`
5. `判定法测试场景`: `判定ID`, `判定名称`, `条件1`, `条件2`, `条件3`, `条件组合`, `预期结果`, `备注说明`
6. `因果图测试场景`: `场景ID`, `场景名称`, `原因1`, `原因2`, `原因3`, `约束关系`, `结果1`, `结果2`, `结果关系`, `测试组合`, `预期结果`, `备注说明`

## `测试用例.xlsx`

Reference-template sheets:

1. `计划`
2. `需求`
3. `SIT`
4. `问题`

### `计划`

Headers:

`测试模块`, `开始时间`, `结束时间`, `负责人`, `技术支持`, `测试明细内容（菜单名称）`, `备注`

Fill one row per test phase (需求分析、编写案例、数据准备、成都测试, etc.). Adjust phases as needed.
Use `YYYY\\MM\\DD` date format. The 测试明细内容 column should list specific test scope items, numbered if multiple.

### `需求`

Headers:

`*交易/产品/功能名称`, `*需求名称`, `*需求描述`, `说明：描述交易的主要输入、输出业务要素；或产品使用的场景（业务流程）`, `*设计人`, ` 设计时间`, `*已审阅`, `*优先级`

Use one or more requirement rows. Keep the requirement name traceable to the change number and title.

**说明列格式规范（强制）**：

说明列必须采用"业务场景＋逐条编号"格式，禁止使用"输入/输出"或"业务流程"概述式写法：

```text
业务场景：
1.<第一条业务要点>
2.<第二条业务要点>
3.<第三条业务要点>
...
```

规则：
- 每条业务要点独立成行，以阿拉伯编号开头
- 每条对应一个可追溯、可测试的业务规则或场景分支
- 涵盖正例、反例、边界值、异常、回归等需要覆盖的场景
- 条目数量与需求文档中可提取的测试点一一对应
- 语言精炼，避免重复描述

### `SIT`

Headers:

`案例主题`, `测试名称`, `类型`, `案例描述`, `案例类型`, `案例层次`, `步骤序号`, `步骤描述`, `预期结果`, `设计者`, `创建日期`, `评审状态`, `截图`

**案例主题命名规范（强制）**：

格式：`系统\变更编号\序号\需求简称`

示例：`微信小程序\CHG202601220055\01\渠道端控制注册年龄`

规则：
- 系统：需求所属系统名称（如微信小程序、手机银行、网贷系统等）
- 变更编号：需求变更单编号
- 序号：从01开始递增，同一变更下若有多组功能可依次编号
- 需求简称：变更编号后面的需求标题简述

**测试名称命名规范（强制）**：

格式：`系统_变更编号需求简称_三位序号`

示例：`微信小程序_CHG202601220055渠道端控制注册年龄_001`

规则：
- 与案例主题保持一致的"系统+变更编号+需求简称"前缀
- 下划线连接前缀与三位序号（001、002、003...）
- 序号按用例顺序递增，不跳号

Layout:

- Merge the case-level columns `A:F` and `J:M` vertically across each case's step rows.
- Keep `G:I` unmerged so each step remains a separate row.
- Center merged case-level content except `案例描述`, which stays left-aligned and wrapped.
- Format `案例描述` as:

```text
测试目的：<案例目的正文>
测试数据：
<测试数据行>
```

## Writing Rules

- Derive rows from explicit requirement points first, then developer cases.
- Keep positive, negative, boundary, and special cases separated.
- Use short, traceable notes instead of long narrative.
- Prefer realistic phone numbers, account names, and transaction names that appear in the source.
- Do not widen scope beyond the source documents.

### `问题`

Headers:

`操作类型/案例编号`, `问题描述/截图`, `测试日期`, `提交人`, `BUG编号`, `处理人`, `处理情况`, `处理日期`, `复测日期`, `复测结果`, `复测问题`, `BUG状态`, `备注`

Add this sheet as a blank template (header only). Testers will fill in rows during execution when bugs are found.

> AI生成
# AR 应收账款实时跟进与回款核对工具 PRD

## 1. 产品概述
AR 应收账款实时跟进与回款核对工具，面向海外诊所财务团队。  
以 SGIMED Invoice 为主数据，结合 TPA Payment Advice、MHCP GOV Claim、银行流水和 Corporate 客户付款信息，对每张 Invoice 的回款状态进行持续跟踪，统一管理已收、未收、部分收款、异常和待核销状态。  

## 2. 背景与目标
- **问题**：现有依赖代理记账季度报表，回款状态滞后，财务需在 SGIMED、MHCP、PA、银行流水间反复核对。
- **目标用户**：财务 AR 负责人、Finance Owner、GOV Claim Owner、CA、管理层、代理记账。
- **MVP目标**：
  - 导入 SGIMED Invoice
  - AR 台账生成
  - 资金来源分类（TPA / GOV / Patient / Corporate）
  - 回款证据导入和匹配
  - 异常识别与跟进
  - AR 看板及导出
- **不做范围**：自动对接 SGIMED/银行/MHCP API，自动催款，自动生成会计分录。

## 3. 用户角色
| 角色 | 权限范围 | 核心诉求 |
|---|---|---|
| 财务 AR 负责人 | 查看/新增/编辑 AR、匹配结果、异常 | 快速知道每张 Invoice 状态 |
| Finance Owner | 查看 TPA / Corporate / 银行流水、编辑匹配 | 核对回款，确认短付差异 |
| GOV Claim Owner | 查看 GOV Invoice / MHCP / 异常 | GOV 回款状态确认 |
| CA | 查看所属诊所 Patient Self-pay | 跟进自付款 |
| 管理层 | 查看汇总指标 | 关注逾期、坏账、回款率 |
| 代理记账 | 查看导出清单 | 完成核销 |

## 4. 核心流程
1. 导入 SGIMED Invoice → 系统生成 AR 主表  
2. 上传 PA / MHCP / 银行流水 → 系统匹配 Invoice  
3. 财务确认匹配结果 → 更新 AR 状态  
4. 异常生成 → 分派负责人 → 跟进记录  
5. 已确认收款导出 → 代理记账核销  
6. 管理层通过看板监控指标  

## 5. 功能需求
- Invoice 导入/台账生成  
- 资金来源分类  
- PA 导入 + 自动匹配 + 短付异常  
- MHCP 底表导入 + Paid/Submitted/Rejected 状态更新  
- 银行流水导入 + Patient / Corporate 匹配  
- 异常清单管理（短付、逾期、Rejected、付款方不明）  
- AR 管理看板（KPI / 资金来源 / 诊所维度）  
- 导出清单（未收、待核销、异常、SOA）  
- 权限与留痕机制  

## 6. 验收标准
- Invoice 导入数量正确  
- 自动匹配结果正确，短付/异常生成  
- 异常清单可操作、分派、跟进  
- AR 看板显示 KPI 正确  
- 导出清单字段完整  

## 7. 风险与依赖
- 数据来源：SGIMED、PA、MHCP、银行流水  
- 权限控制与数据安全  
- 用户是否按流程操作  
- 异常和 Write-off 审批机制

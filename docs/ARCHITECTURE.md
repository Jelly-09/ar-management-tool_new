# AR 应收账款管理工具 ARCHITECTURE

## 1. 技术栈
- 前端：React + Vite + Tailwind + shadcn/ui
- 图表：Recharts
- 后端：Node.js / Flask（可选）
- 数据库：PostgreSQL / Supabase
- 文件存储：本地 / 对象存储
- 部署：Vercel / 内网服务器

## 2. 模块划分
- 前端：
  - DashboardPage
  - InvoiceLedgerPage
  - MatchingPage
  - ExceptionPage
  - ExportPage
  - Toolbar + 搜索筛选组件
- 后端：
  - 导入/解析 Excel / CSV
  - 数据匹配规则
  - API 接口：获取 AR 列表、更新状态、导出
- 数据库：
  - Invoice 表
  - PA 表
  - MHCP Claim 表
  - Bank Transaction 表
  - Exception 表
  - 用户表 + 角色表

## 3. 数据流
1. 财务上传 SGIMED Invoice → 存入 Invoice 表  
2. 上传 PA / MHCP / 银行流水 → 存入对应表  
3. 系统匹配规则 → 更新 Invoice 状态 + 异常生成  
4. 用户操作异常 / 更新状态 → 写入日志  
5. 导出 → Excel / CSV / SOA  

## 4. 部署约定
- 前端静态页面：Vercel / 内网 Nginx
- 后端 API：云服务器或内网服务
- 数据库：Supabase / PostgreSQL
- 文件：对象存储或数据库附件
- 权限控制：基于角色 + 字段可见性
- 日志记录：操作留痕

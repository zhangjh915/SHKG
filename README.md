# 🏫 上海浦东新区幼儿园地图

基于 2025 年招生地段公示数据，展示浦东新区 468 所幼儿园的交互式地图。

🔗 [在线预览](https://zhangjh915.github.io/SHKG/)

## 功能

- **地图浏览**：高德地图展示幼儿园位置，按办园等级着色
- **名称搜索**：搜索幼儿园名称，结果列表点击可定位
- **家庭地址定位**：输入地址（小区名/路名均可），自动按距离排序，下拉联想候选
- **多维筛选**：按办园等级（示范园/一级/二级等）和保育费上限筛选
- **手机适配**：移动端可收起面板，全屏查看地图

## 项目结构

```
SHKG/
├── index.html              # 前端页面
├── data.json               # 幼儿园数据（坐标、等级、费用等）
├── process_data.py         # 数据处理脚本（Excel → data.json）
├── manual_overrides.json   # 手动修正的坐标（优先于 API 搜索）
├── failed_kindergartens.txt # 定位失败的幼儿园列表
└── 上海浦东新区幼儿园2025.xls # 原始 Excel 数据
```

## 更新数据

### 1. 准备 Excel

将最新招生公示 Excel 放在项目目录，确保格式与当前文件一致（序号、幼儿园名称、招生地段、小区名称、保育教育费、办园等级）。

### 2. 运行脚本

```bash
pip install pandas openpyxl xlrd requests
python3 process_data.py
```

### 3. 手动修正

如果部分幼儿园定位不准：
- 编辑 `manual_overrides.json`，按格式添加坐标
- 重新运行脚本即可生效

## 技术栈

- 高德地图 JS API v2.0
- 高德 Web 服务 API（POI 搜索、地理编码、InputTips）
- 纯前端 HTML/CSS/JS，无框架依赖

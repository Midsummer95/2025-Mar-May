# 目录结构
2023-Mar-May/
├── .github/                  # GitHub专属配置
│   ├── workflows/            # CI/CD流水线
│   │   └── deploy.yml        # 自动部署配置
│   └── ISSUE_TEMPLATE/       # 问题模板
│       └── weekly-report.md  # 周报模板
│
├── docs/                     # 知识沉淀
│   ├── browser/              # 浏览器原理笔记
│   ├── react/                # React深度解析
│   ├── engineering/          # 工程化实践
│   └── assets/               # 图床资源
│       └── week1-arch.png    # 架构图等
│
├── projects/                 # 实战项目
│   ├── mini-react/           # 手写React核心
│   │   └── packages/         # Monorepo结构
│   ├── performance-sdk/      # 性能监控SDK
│   └── component-lib/        # 组件库
│
├── weekly/                   # 周任务追踪
│   ├── week-01/              # 每周独立目录
│   │   ├── src/             # 当周代码
│   │   ├── notes/           # 学习笔记
│   │   ├── screenshots/     # 成果截图
│   │   └── REVIEW.md        # 周度复盘文档
│   └── week-02/
│
├── templates/                # 模板文件
│   ├── react-component/      # 组件模板
│   └── node-module/          # Node模块模板
│
├── scripts/                  # 自动化脚本
│   ├── auto-deploy.sh        # 部署脚本
│   └── code-check.sh         # 代码检查
│
├── .gitignore                # 忽略规则
├── README.md                 # 项目门户
└── ROADMAP.md                # 学习路线图

关键目录详解：
1. .github/
  包含GitHub Actions工作流配置
  建议预置代码质量检查流水线（ESLint+Jest）
  添加PR模板规范提交信息

2. docs/
采用「主题+时间」双维度管理：
docs/react/
├── 01-fiber-architecture.md
├── 02-hooks-mechanism.md
└── diagrams/            # 配套示意图

3. weekly/
每周目录命名规范：
week-[num]-[theme]  # 示例：week-03-react-fiber
每个周目录包含：
  CHANGELOG.md 记录每日进展
  problems.md 技术难点归档

4. projects/
采用Monorepo结构管理关联项目：
projects/mini-react/
├── packages/
│   ├── reconciler/     # 协调器实现
│   └── renderer/       # 渲染器实现
└── playground/         # 演示案例

分支策略
- main       : 仅存放稳定版本
- dev        : 日常开发分支
- feat/*     : 功能开发分支
- weekly/*   : 周任务专属分支


# 维护建议：
目录清理周期
每周目录保留最近8周内容
每月归档历史内容到archive/目录

### 文件命名规范
- 代码文件 : kebab-case（例：virtual-list.tsx）
- 文档文件 : 01-topic-name.md（序号+主题）
- 资源文件 : yyyymmdd-description.png（日期+描述）

### 智能检索优化
在README添加搜索标签：
<!-- TAGS: react, browser, 性能优化 -->

# 项目初始化

### 创建基础结构
mkdir -p 2025-Mar-May/{.github/{workflows,ISSUE_TEMPLATE},docs/{browser,react,engineering,assets},projects,weekly,templates,scripts}

### 添加基础文件
touch README.md ROADMAP.md .gitignore
echo "node_modules\n.DS_Store\ndist" > .gitignore

### 删除目录的误跟踪文件（如果有的话）
git rm --cached package*
git rm -r --cached node_modules

### 创建.gitignore防止误添加
echo "node_modules/" > .gitignore
echo "package-lock.json" >> .gitignore

### 初始化Git
git init


### 1. Git Hook增强
#### 安装Husky
npx husky install
npx husky add .husky/pre-commit "npm run lint"

### 2. 文档自动化
#### 使用VitePress快速搭建文档站
npm install vitepress --save-dev
mkdir docs/.vitepress

# 初次提交代码
### 查看所有本地分支（带星号的是当前分支）
git branch
### 将master分支重命名为main
git branch -m master main
### 创建初始提交（如果尚未提交）
git add .
git commit -m "chore: initialize repository structure"
### 第一步：在GitHub创建空仓库
### 第二步：本地仓库关联远程仓库
#### 添加远程仓库地址（注意替换你的用户名）
git remote add origin https://github.com/Midsummer95/2025-Mar-May.git
### 第三步：首次推送代码
### 强制推送本地分支到远程（仅首次需要-f参数）
git push -u -f origin main
### 常规推送（后续操作）
git push
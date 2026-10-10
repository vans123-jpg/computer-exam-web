# 山东专升本 · 计算机刷题（近五年）

纯前端静态刷题网页，**无需后端、无需数据库**，打开即用，适合手机和电脑。

## 功能

- ✅ **单选题 / 多选题**：单选点选即答，多选漏选错选均判错
- ✅ **提交判分**：点“提交答案”立即判对错
- ✅ **解析展示**：每题提交后展示中文详细解析，且解析中包含**全部选项（A/B/C/D）的逐项解读**（正确项为什么对、错误项错在哪里）
- ✅ **错题本**：答错自动加入错题本，答对自动移出，数据保存在浏览器 localStorage（刷新、关机都不丢）
- ✅ **筛选**：按年份（2022–2026）、知识点、题型筛选题目
- ✅ **三种模式**：顺序练习 / 随机练习 / 错题重练
- ✅ **答题卡 + 统计**：答题卡跳题、进度条、交卷成绩单
- ✅ **手机端适配**：响应式布局、底部吸底操作栏、大触控区域

## 题库说明

`questions.json` 共 **190 题**（单选 147 / 多选 43），覆盖 2022–2026 年：

- 各年真题改编的单选、多选题
- **2022、2023、2024 年真题填空题**全部改编为单选题（题干标注“真题·填空题改编”）
- **2023 年真题分析题**改编为单选题（数据透视表、流程图、Word 导航窗格等）
- **论述题（简答题）真题**改编为单选 / 多选题（题干标注“论述题真题改编”）
- **山东各大机构公开模拟题 / 每日一练**（题干标注机构来源）：
  - 山东专升本网（zsb.sd.cn）计算机模拟试题 · 3 题
  - 传爱专升本（专升本考试网 zsbedu.com.cn）山东计算机练习题（7.08 填空改编 + 7.13 单选）· 10 题
  - 中公专升本（offcnzsb.com）计算机每日一练（2023.2.10 / 2023.5.23 / 2023.9.7 / 2024.1.15）· 15 题

字段说明：`year`（年份）、`type`（题型）、`knowledge_point`（知识点）、`question`（题干）、`options`（选项数组）、`answer`（答案，如 `A`、`ABD`）、`analysis`（解析。每条解析末尾均附【选项分析】，逐项说明 A/B/C/D 各选项为什么正确或错误）。

> 网页通过 `fetch('./questions.json')` 读取同目录题库，**四个文件必须放在同一目录下**。

---

## 一、本地预览方法

> ⚠️ 注意：由于浏览器安全限制，**不能直接双击 index.html（file:// 协议）打开**，否则读不到 questions.json。必须用本地服务器方式访问，任选一种：

### 方法 1：VS Code + Live Server（推荐，最简单）

1. 安装 [VS Code](https://code.visualstudio.com/)
2. 扩展商店搜索 **Live Server** 并安装
3. 用 VS Code 打开本文件夹，右键 `index.html` → **Open with Live Server**
4. 浏览器自动打开 `http://127.0.0.1:5500`，即可刷题

### 方法 2：Python（电脑自带或装了 Python 即可）

在本目录打开命令行（文件夹地址栏输入 `cmd` 回车），执行：

```bash
python -m http.server 8000
```

然后浏览器访问 `http://localhost:8000`

### 方法 3：Node.js

```bash
npx serve
```

按提示的地址（通常是 `http://localhost:3000`）访问即可。

---

## 二、部署到 Vercel 获取在线网址（完整步骤）

Vercel 免费、无水印、支持自动 HTTPS，三选一种方式：

### 方式 A：命令行一键部署（最快，推荐）

1. 安装 Node.js 后，在本目录打开命令行，执行：

   ```bash
   npm i -g vercel
   ```

2. 登录（首次会跳转浏览器授权，没有账号可用 GitHub 账号免费注册）：

   ```bash
   vercel login
   ```

3. 在**本项目目录内**执行部署（一路回车即可）：

   ```bash
   vercel
   ```

4. 看到 `✔ Production: https://你的项目名.vercel.app` 即部署成功，复制该网址即可访问。

5. 以后改完 `questions.json` 或 `index.html`，再执行一次 `vercel --prod` 即可更新线上版本。

### 方式 B：网页拖拽部署（不用装任何东西）

1. 打开 https://vercel.com ，用 GitHub / Google / Email 免费注册登录
2. 点击 **Add New… → Project**
3. 把本文件夹里的 4 个文件（`index.html`、`questions.json`、`vercel.json`、`README.md`）直接**拖拽上传**（或先压成 zip）
4. Framework Preset 选 **Other**，无需修改任何配置，点 **Deploy**
5. 等待约 30 秒，出现绿色 ✅ 后点击 **Visit**，即可拿到形如
   `https://xxx.vercel.app` 的在线网址

### 方式 C：GitHub 仓库 + Vercel 关联（可自动更新）

1. 注册 https://github.com ，新建仓库并上传这 4 个文件：

   ```bash
   git init
   git add .
   git commit -m "init"
   git branch -M main
   git remote add origin https://github.com/你的用户名/仓库名.git
   git push -u origin main
   ```

2. 打开 https://vercel.com → **Add New… → Project** → **Import** 刚才的仓库
3. Framework Preset 选 **Other**，Build Command 留空，点 **Deploy**
4. 部署完成后得到在线网址；以后每次 `git push`，Vercel 都会**自动重新部署**最新版本

---

## 三、如何扩充/修改题库

直接用记事本或 VS Code 编辑 `questions.json`，按同样格式追加对象即可：

```json
{
  "year": 2026,
  "type": "单选题",
  "knowledge_point": "计算机基础知识",
  "question": "题干内容？",
  "options": ["选项一", "选项二", "选项三", "选项四"],
  "answer": "A",
  "analysis": "解析内容"
}
```

字段说明：

- `type`：只能是 `单选题` 或 `多选题`
- `answer`：单选为 `A`~`D` 中一个字母；多选为字母组合，如 `ABD`（按 A、B、C、D 顺序，无空格）
- `options`：选项数组，单选 4 个，多选一般 4 个
- `year`：数字，如 `2026`
- 每个对象之间用逗号隔开，最后一个对象后**不要**加逗号

修改保存后刷新页面即可生效（线上部署需重新 `vercel --prod` 或 push 触发更新）。

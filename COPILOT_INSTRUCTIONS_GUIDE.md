# Copilot Instructions 使用说明

`copilot-instructions.md` 是 GitHub Copilot 的行为指令文件，用于约束 AI 的编码习惯，减少过度设计、无效改动等常见问题。

---

## 作用范围

| 类型 | 位置 | 作用范围 |
|------|------|---------|
| 仓库级 | `<项目>/.github/copilot-instructions.md` | 仅当前项目 |
| 用户级 | VS Code / VS 设置中配置绝对路径 | 本机所有项目 |

---

## 在 Visual Studio Code 中使用

### 仓库级（当前项目自动生效）

将文件放在项目根目录的 `.github/` 文件夹下即可，无需任何配置：

```
your-project/
└── .github/
    └── copilot-instructions.md   ← 放这里，打开项目自动生效
```

### 用户级（所有项目生效）

1. 打开设置：`Ctrl + ,`
2. 搜索：`copilot instructions`
3. 找到 **GitHub Copilot Chat › Chat: Code Generation Instructions**
4. 点击 **Edit in settings.json**，添加：

```json
"github.copilot.chat.codeGeneration.instructions": [
    {
        "file": "C:/Users/yourname/instructions/copilot-instructions.md"
    }
]
```

> `file` 填写指令文件的绝对路径。

---

## 在 Visual Studio 中使用

### 仓库级（当前项目自动生效）

与 VS Code 相同，将文件放在 `.github/copilot-instructions.md`，Visual Studio 2022 17.10+ 会自动读取。

### 用户级（所有项目生效）

1. 打开菜单：**Tools → Options**
2. 导航到：**GitHub Copilot → General**
3. 在 **Custom Instructions** 一栏，填入指令文件的绝对路径

---

## 在新项目中引入

**方式一：手动复制**

```sh
# 复制到新项目
cp .github/copilot-instructions.md <新项目路径>/.github/copilot-instructions.md
```

**方式二：GitHub 模板仓库**

在 GitHub 仓库设置中勾选 **Template repository**，之后新建项目时选择此模板，文件自动带入。

---

## 验证是否生效

在 Copilot Chat 中发送：

```
What instructions are you following for this project?
```

Copilot 会列出当前生效的 instructions 来源，确认文件已被加载。

---

## 文件内容说明

指令文件位于 `.github/copilot-instructions.md`，包含四条核心准则：

| 准则 | 核心约束 |
|------|---------|
| **Think Before Coding** | 不假设，不隐藏困惑，有歧义先问 |
| **Simplicity First** | 只实现被要求的，不写推测性代码 |
| **Surgical Changes** | 只动必须动的地方，不顺手优化 |
| **Goal-Driven Execution** | 先定义可验证目标，再写代码 |

# inkjun-writer

一个纯 Markdown 驱动的公众号长文写作 Skill。

这个仓库现在只保留两类核心内容：

- `SKILL.md` 里的 4 种写作模式
- `references/rewrite-few-shots.md` 里的 few-shot 改写规则

## 设计原则

- 轻量：只保留真正影响写作输出的规则
- 可移植：整个 skill 直接放在仓库根目录，方便复制和分发
- 可协作：先讨论，再起草，再改稿，而不是一上来机械生成全文

## 仓库结构

```text
.
├── README.md
├── SKILL.md
├── tests/
│   ├── README.md
│   ├── cases/
│   │   ├── discuss/
│   │   ├── outline/
│   │   ├── draft/
│   │   └── rewrite/
│   │       └── keep-core-judgment/
│   │           ├── input.md
│   │           ├── notes.md
│   │           └── output.md
│   └── templates/
│       └── case/
│           ├── input.md
│           ├── notes.md
│           └── output.md
└── references/
    └── rewrite-few-shots.md
```

## 文件说明

- `SKILL.md`：技能主文件，包含适用/不适用边界、4 种模式、改稿深度与输出自检要求
- `references/rewrite-few-shots.md`：记录高频句法问题、L0/L1/L2 分级、Gate 门禁与 few-shot 改写示例
- `tests/`：放手动测试 skill 的样例，不参与 skill 本体定义

## 测试目录约定

为了方便后续持续测试，推荐把测试样例按模式放进 `tests/cases/<mode>/<case-name>/`：

- `input.md`：测试输入
- `output.md`：期望输出，或当前一版可接受输出
- `notes.md`：测试目的、关注点、使用方式、通过标准

这样做的好处很直接：

- skill 定义和测试样例分离，不会把根目录越堆越乱
- 先按模式分层，再按 case 拆分，后续补场景时不会混在一起
- 每个测试 case 可以单独演进，方便比较不同版本输出

建议优先按“要验证的能力”或“要防的退化”命名 case，例如：

- `rewrite/keep-core-judgment`
- `rewrite/reduce-ai-tone`
- `draft/from-outline`
- `outline/opinion-article`
- `rewrite/reduce-verbosity`

新增测试时，直接复制 `tests/templates/case/` 最省事。

## 这个 Skill 能做什么

适合这些场景：

- 你想写一篇公众号长文，但主题还没聊清楚
- 你有零散素材，想整理成可发文章
- 你已经有初稿，想让它更有结构、更有判断、更不像 AI 写的

## 使用方式

把这个仓库作为一个本地 skill 使用时，核心入口就是 `SKILL.md`。

典型流程是：

1. 根据用户诉求进入讨论、提纲、起草或改稿模式
2. 如果进入起草或改稿模式，额外读取 `references/rewrite-few-shots.md`
3. 用 few-shot 约束句法，避免预制转折和模板感

测试改稿模式时，可以直接针对某个 case 运行，例如：

`参考 SKILL.md 和 references/rewrite-few-shots.md，把 tests/cases/rewrite/keep-core-judgment/input.md 改写到 tests/cases/rewrite/keep-core-judgment/output.md`

## 为什么不用额外工具

这个 skill 刻意不引入脚本、数据库或复杂配置，原因很直接：

- Markdown 更容易被人理解和修改
- 拷贝到别的仓库时几乎没有迁移成本
- few-shot 规则可以直接人工检查，不会变成黑盒

## 适合继续扩展的方向

如果后续需要，依然可以保持 Markdown 驱动，继续扩展：

- 增加更多高价值 few-shot
- 增加不同文章类型的提纲提示
- 增加少量标题或开头参考

但默认建议先保持轻量，不要过早做重。

# Tests

这里放的是用于手动测试 `SKILL.md` 的样例。

当前仓库的测试不是自动化单测，而是面向 skill 输出行为的 case 测试。
为了避免样例越堆越乱，统一按“模式 -> case”组织。

## 目录约定

```text
tests/
├── README.md
├── cases/
│   ├── discuss/
│   ├── outline/
│   ├── draft/
│   └── rewrite/
└── templates/
    └── case/
        ├── input.md
        ├── notes.md
        └── output.md
```

推荐把 case 放进这些模式目录：

- `tests/cases/discuss/`：讨论模式
- `tests/cases/outline/`：提纲模式
- `tests/cases/draft/`：起草模式
- `tests/cases/rewrite/`：改稿模式

## 一个 case 里放什么

每个 case 目录保留 3 个文件：

- `input.md`：测试输入
- `output.md`：一版可接受输出，或当前参考输出
- `notes.md`：测试目标、关注点、运行方式、通过标准

其中 `notes.md` 比 `output.md` 更重要。
因为写作输出并不总是唯一，`output.md` 更像参考答案，`notes.md` 才是真正的验收标准。

## 命名建议

case 名优先写“要防的退化”或“要验证的能力”，不要只写 `demo`。

例如：

- `discuss/audience-positioning`
- `outline/opinion-article`
- `draft/from-outline`
- `rewrite/keep-core-judgment`
- `rewrite/reduce-ai-tone`
- `rewrite/compress-length`

## `notes.md` 建议至少写清楚

- 当前 case 对应哪个模式
- 输入材料是什么类型
- 这次主要验证什么
- 哪些内容必须保留
- 哪些问题必须被修掉
- 输出允许有哪些非唯一变化

## 新增 case 的推荐方式

直接复制 `tests/templates/case/`，再放进对应模式目录，例如：

```text
tests/cases/rewrite/keep-core-judgment/
```

然后补齐 `input.md`、`output.md` 和 `notes.md`。

## 当前已覆盖的示例

- `discuss/audience-positioning`：测试讨论模式下的受众定位和主线建议
- `outline/opinion-article`：测试提纲模式下的观点型长文结构设计
- `draft/from-outline`：测试起草模式下从提纲扩成完整长文
- `rewrite/keep-core-judgment`：测试改稿模式下保留核心判断
- `rewrite/reduce-ai-tone`：测试改稿模式下减少模板腔和 AI 腔
- `rewrite/compress-length`：测试改稿模式下压缩冗余、提升信息密度
- `rewrite/reduce-verbosity`：测试改稿模式下消除重复兜圈和解释性铺垫

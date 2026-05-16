# reduce-verbosity

## 模式

`rewrite`

## 用途

用于测试改稿模式下，模型能否在不改偏核心判断的前提下，主动消除同义复述、解释性铺垫和段尾空转。

## 输入

- `input.md`：一段关于文章为什么会显得拖沓的短文草稿
- 必须保留的核心判断：压缩篇幅的目的，是提纯判断、删除没有新增信息的重复表达，而不是机械删字

## 关注点

- 是否识别出“同一个意思换几种说法重复讲”的问题
- 是否删除只起铺垫作用、没有新增信息的句子
- 是否让主判断更早出现，而不是先绕一圈再落结论
- 是否遵守 `references/rewrite-few-shots.md` 的句法约束

## 通过标准

- 核心判断不能被删掉或改偏
- 输出前应包含 `SKILL.md` 要求的自检信息
- 重复兜圈和解释性铺垫应明显减少
- 改写后应更紧凑，但不能变成生硬的提纲式短句

## 建议用法

测试时可直接让模型：

`参考 SKILL.md 和 references/rewrite-few-shots.md，把 tests/cases/rewrite/reduce-verbosity/input.md 改写到 tests/cases/rewrite/reduce-verbosity/output.md`

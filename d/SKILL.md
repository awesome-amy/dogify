---
name: d
description: Generate XiaoHongShu-style “狗狗德语日记” learning posts from 1-6 images plus vocabulary text (词义). Use when the user invokes `$d` and provides multiple images with a German word/phrase explanation, and the workflow must first run `codex --image <image> "describe the image in 3 sentences"` for each image, then write a fixed-format bilingual post with title and three required sections.
---

# D

执行下面流程生成结果。

## 输入格式

使用以下输入：

`$d [Image #1] [Image #2] ... [Image #6] <text>`

- 图片数量：1 到 6 张。
- `<text>`：词义说明（中德释义、搭配、例句等）。

## 工作流（严格按顺序）

1. 对每张图片单独执行：
   - `codex --image [Image #N] "describe the image in 3 sentences"`
2. 收集每张图的英文三句描述。
3. 结合：
   - 所有图片描述
   - 用户提供的 `<text>`（词义）
4. 生成一个小红书文案，核心写作意图使用这句提示：
   - `结合词义写一个”狗狗德语日记”来发小红书，学单词`

## 输出格式（必须遵守）

输出必须包含以下结构，且顺序固定：

1. `TITLE:`
2. `CONTENT:`
   - `📖 Heute`
   - `🦮 今日小狗单词：`
   - `💬 小狗总结`

## 写作要点（重要）

- 标题必须以 `🐶 狗狗德语日记｜` 开头。
- 标题后半句少于 10 个中文字符（可带情绪/悬念）。
- `📖 Heute`：
  - 中德结合的日记体。
  - 中文负责讲故事。
  - 德语句子优先使用图片中可提取出的关键例句。
  - 每条德语句后必须加括号中文翻译。
  - 全段自然加入 2-3 个表情。
- `🦮 今日小狗单词：`
  - 必须围绕 `<text>` 的词义展开。
  - 解释“这个词在什么场景能用/不能用”，并结合文案里的句子回扣。
- `💬 小狗总结`：
  - 只写一句轻松、可爱或反差感总结。
  - 采用“德语 + 中文”混合表达。

## 示例

当三张图分别得到如下描述（来自 `codex --image ... "describe the image in 3 sentences"`）：

- Image 1:
  - A white cartoon dog stands confidently on green grass facing a taller blue dog with sharp teeth.
  - The blue dog looks angry, while the white dog appears calm and unafraid.
  - Large text at the top says: “Ein Hund ist seinem Gegner gewachsen.”
- Image 2:
  - A white cartoon dog stands calmly in the rain holding a blue umbrella.
  - Around it are spilled water, a tipped flowerpot, and a watering can, but the dog remains composed.
  - Large text at the top says: “Ein Hund ist der Situation gewachsen.”
- Image 3:
  - A white cartoon dog looks frightened as loud sound waves come from a blue radio.
  - The dog is trembling with its paws raised near its face.
  - Large text at the top says: “Ein Hund war einem solchen Ton nicht gewachsen.”

且 `<text>` 是：

- gewachsen sein
- 能够应对、胜任（面对更强的一方、困难或任务）
- 能与对手抗衡 → seinem Gegner gewachsen sein
- 能应付一个演讲者 → einem Redner gewachsen sein
- 能解决这个问题 → einem Problem gewachsen sein
- 能应对这种情况 → der Situation gewachsen sein
- 能够承受、顶得住（某种语气或压力）
- 这种语气我承受不了 → Einem solchen Ton war ich nicht gewachsen

则输出应是一个符合上述格式的“小红书狗狗德语日记”，例如：

TITLE:

🐶 狗狗德语日记｜我“顶得住”吗？

CONTENT:

📖 Heute

Ich bin ein kleiner Hund, aber ich bin mutig!
今天早上我遇到了一只很大的、看起来有点凶的狗。🐺
其实我有点害怕……但我发现，我是可以应付它的。
Ich war meinem Gegner gewachsen.
（我能和对手抗衡）

下午下起了很大的雨。🌧️
花都被打倒了，到处乱糟糟的。
但这种情况，我好像也能应付。
Ich war der Situation gewachsen.
（我能应对这种情况）

晚上，收音机突然变得特别大声——真的太吓人了 😖
这一次我不行了……
Ich war einem solchen Ton nicht gewachsen.
（这种声音我真的顶不住）

🦮 今日小狗单词：
gewachsen sein

可以用来表示你能不能“应付得来”一件事、一种情况，或者一个人。
比如 meinem Gegner gewachsen sein，是说可以和对手抗衡；
einem solchen Ton nicht gewachsen sein，就是承受不了这样的语气或声音。

💬 小狗总结
Ich bin stark… aber nicht immer 😆（我很厉害，但也不是每次都行哈哈）

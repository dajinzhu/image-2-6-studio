# Image 2.6 Studio

一个给 Codex 使用的生图 Skill：把简单的商品图、广告图需求整理为明确的生成或改图指令，生成后再检查主体、文字和参考图一致性。

## 安装

在 Codex 对话里发送：

~~~text
$skill-installer install https://github.com/dajinzhu/image-2-6-studio/tree/main/skills/image-2-6-studio
~~~

安装完成后，在下一轮对话调用即可。也可以打开仓库中的 [SKILL.md](skills/image-2-6-studio/SKILL.md) 查看完整说明。

## 开始使用

~~~text
使用 $image-2-6-studio，为一个无品牌的琥珀色香薰蜡烛制作一张暖色窗边商品图。画面横版，标签留白，不要文字或 Logo。
~~~

已有商品照片时，附上原图，再说明需要修改的背景，以及必须保留的包装、形状、颜色和文字。

默认使用当前 Codex 可用的内置生图工具，通常不需要 API 密钥。**内置工具未必显示具体模型版本，不能据此保证每张图都由 Image 2.6 生成。**如需明确指定 GPT Image 2.6，可阅读 [API 使用说明](skills/image-2-6-studio/references/api-mode.md)，选择已有的系统 imagegen CLI。API 调用需要自行配置密钥与访问权限，可能产生费用。

## 示例：同一款虚构蜡烛的场景修改

| 初始商品图 | 窗边场景图 |
| --- | --- |
| ![琥珀色蜡烛的棚拍示例](examples/01-candle-studio.png) | ![琥珀色蜡烛的窗边场景示例](examples/02-candle-lifestyle.png) |

两张都是为教程生成的虚构商品图，并非客户原片或成交案例。它们由本次 Codex 内置生图工具生成；该接口未返回可核实的模型版本。查看[实际使用的提示词](examples/prompts.md)。

## 使用边界

真实客户项目请使用有权处理的素材，检查生成结果中的商品外观、标签和文字，并按客户及发布平台的要求确认使用方式。你可以将这个 Skill 安装到自己的 Codex 中使用。

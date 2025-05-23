# 有监督微调

有监督微调（Supervised Fine-Tuning），简称 SFT，是将预训练模型往特定领域或任务迁移的一个重要过程。虽然预训练模型总体性能也很不错，但如果需要应对特定场景，就必须针对场景进行定制化。SFT 通过在人工筛选的高质量数据上进一步训练，将预训练模型往特定任务上迁移。

## SFT 原理简介

SFT 核心思想是让预训练模型学习标注过的、特定领域的数据。这个过程会向模型提供很多我们想要的输入-输出，让模型去学习我们想要的特定回答模式。

由于利用了预训练模型学到的基础知识，通过 SFT 将模型进一步适配到特定领域的训练还是非常高效的。

## 什么时候使用 SFT

SFT 通常在你当前模型的能力和你的特殊需求还存在差距时使用，尤其是当你想要精细控制模型输出，或是想让模型在特定领域发挥作用时。

举例来说，如果你在开发客户服务相关的应用，那你可能需要让模型严格遵循公司规定、用标准化的流程去处理技术性的咨询。或者，在医疗或法律领域，准确表达特定领域的专业术语也很重要。在这些情况下，SFT 就能将模型性能对齐到领域内专家的水平，使得模型的回答符合专业标准。

## 微调的过程

SFT 主要就是在特定任务的数据集上训练模型。

首先，你需要准备一个能反映任务类型的数据集，这个数据集需要涵盖尽可能广泛的领域内问答场景。数据的质量非常重要，每条数据都应该向模型展示你希望得到的回答类型。接下来就是实际微调阶段了，你可以使用 HuggingFace 的 `transformers` 和 `trl` 在数据集上训练模型。

整个过程中，不断地对模型进行评测也是很重要的。你可以找一个验证集，然后实时监控模型性能，来确保模型学到了特定领域内的回答，同时又不丧失它原有的通用能力。在[第四章](../4_evaluation)，我们将讲解如何评测模型。

## 通过 SFT 对齐特定偏好

此外，SFT 也广泛用于将语言模型对齐到特定的人类偏好上。如 RLHF 和 DPO 等技术依靠 SFT 来形成对任务的基本理解，然后再进一步对模型的响应进行优化，以达到预期效果。预训练模型，尽管在通用的语言能力上效果很强，但它的回答可能不符合人类的偏好。SFT 通过引入专业领域的数据进行指导，可以改善模型生成与人类期望的匹配程度。

## 使用 Transformer Reinforcement Learning 进行 SFT

TRL（Transformer Reinforcement Learning）是常用于 SFT 的一个重要的软件包。如果你使用强化学习训练 transformer 系列的语言模型，TRL 将为你提供有用工具。

TRL 基于 HuggingFace 的 `transformers` 构建，允许用户直接载入预训练模型，并支持大部分 decoder 或 encoder-decoder 的架构。这个库涵盖了针对语言模型的主流强化学习算法，包括 SFT、奖励模型、PPO、DPO 等。在本课程中，我们将大量使用 TRL。

# 接下来的学习

请通过下列 notebook 上手 SFT：

⏭️ [聊天模板教程](./notebooks/chat_templates_example_cn.ipynb)

⏭️ [有监督微调教程](./notebooks/supervised_fine_tuning_tutorial_cn.ipynb)
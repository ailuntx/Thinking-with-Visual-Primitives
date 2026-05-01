<!-- markdownlint-disable first-line-h1 -->
<!-- markdownlint-disable html -->
<!-- markdownlint-disable no-duplicate-header -->

<div align="center">
  <img src="images/logo.svg" width="60%" alt="DeepSeek LLM" />
</div>
<hr>

<div align="center">
<h1>Thinking with Visual Primitives</h1>

</div>

<div align="center">

  <a href="https://www.deepseek.com/" target="_blank">
    <img alt="Homepage" src="images/badge.svg" />
  </a>
  </a>
  <a href="https://huggingface.co/deepseek-ai" target="_blank">
    <img alt="Hugging Face" src="https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-DeepSeek%20AI-ffc107?color=ffc107&logoColor=white" />
  </a>

</div>

<p align="center">
  <a href="./README.md"><b>English</b></a> |
  <a href="./README_zh.md"><b>简体中文</b></a>
</p>


<div align="center">

  <a href="LICENSE-CODE">
    <img alt="Code License" src="https://img.shields.io/badge/Code_License-MIT-f5de53?&color=f5de53">
  </a>
  <a href="LICENSE-MODEL">
    <img alt="Model License" src="https://img.shields.io/badge/Model_License-Model_Agreement-f5de53?&color=f5de53">
  </a>
</div>


<p align="center">
  <a href="#2-license"><b>📜 许可证</b></a> |
  <a href="#3-citation"><b>📖 引用</b></a> <br>
  <!-- 📄 Paper Link (<a href=""><b>Thinking with Visual Primitives</b></a> | -->

</p>

> [!IMPORTANT]
> 本仓库最初来自一个此前与 `charlesCXK` 相关、目前已不可访问的源仓库。
>
> 原始 upstream / fork 关系已无法可靠保留，因此本仓库应被视为社区镜像/归档，而不是权威官方来源。
>
> 目前尚未发现该项目新的官方替代仓库。请关注以下来源的后续更新，或等待项目后续重新发布：
>
> - `charlesCXK` 主页：https://github.com/charlesCXK
> - DeepSeek 组织：https://github.com/deepseek-ai


## 最新动态

**2026.04.30**：该项目发布了介绍其方法的[技术报告](./Thinking_with_Visual_Primitives.pdf)。后续计划公开内部基准测试，以及部分冷启动数据。模型权重未来将整合进其基础模型，并在之后发布。



## 1. 项目简介
尽管近来的多模态大语言模型（MLLM）在弥合*"感知鸿沟"*方面已经取得显著进展（例如借助高分辨率裁剪，或在图像上进行思考），它们在复杂结构化推理上仍然存在明显短板。该项目将这一瓶颈归因于 **Reference Gap（指代鸿沟）**：自然语言本身过于模糊，难以精确指向稠密的空间布局，因此常常导致推理过程中的逻辑崩溃与幻觉。

本项目提出了一种范式转变。模型不再只是“看得更清楚”，而是学会了**“边推理，边指向”**。通过在推理轨迹中直接交织空间标记（点与边界框），并将其作为*最小思维单元*，该方法能够把抽象的语言概念锚定到具体的物理坐标上。

<table align="center">
  <tr>
    <td align="center" valign="top">
      <img src="./images/coffee.gif" style="height:250px; width:auto; max-width:none;" /><br>
      <b>有锚点的任务推理</b>
    </td>
    <td align="center" valign="top">
      <img src="./images/maze.gif" style="height:250px; width:auto; max-width:none;" /><br>
      <b>拓扑推理</b>
    </td>
  </tr>
</table>


### 核心亮点

*  **点到推理的协同机制：** 受人类认知行为启发（例如用手指计数或沿迷宫路径追踪），该框架将视觉基元提升为最小思维单元，从而有效解决复杂结构化推理中的 Reference Gap。
*  **极致的视觉 Token 效率：** 基于 DeepSeek-V4-Flash 架构，该方法将每 4 个视觉 token 的 KV cache 压缩为单一条目，在保持认知深度的同时，大幅降低图像 token 消耗。
*  **与前沿模型竞争的表现：** 尽管模型规模更紧凑、图像 token 预算也显著更低，该模型仍能在具有挑战性的计数与空间推理基准上，与 **GPT-5.4、Claude-Sonnet-4.6 和 Gemini-3-Flash** 等前沿模型相匹敌。（需要说明的是，文中报告的分数仅覆盖与本文研究重点直接相关的部分评测维度，因此并不能代表这些模型的整体能力。）


<div align="center">
<img alt="image" src="images/teaser.png" style="width:90%;">
</div>






<a id="2-license"></a>
## 2. 许可证

本代码仓库遵循 [MIT License](https://github.com/deepseek-ai/DeepSeek-LLM/blob/HEAD/LICENSE-CODE)。

<a id="3-citation"></a>
## 3. 引用

```bibtex
@article{lu2026think,
  title={Thinking with Visual Primitives},
  author={Lu, Ruijie and Ma, Yiyang and Chen, Xiaokang and Luo, Lingxiao and Wu, Zhiyu and Pan, Zizheng and Liu, Xingchao and Lin, Yutong and Li, Hao and Liu, Wen and Hao, Zhewen and Gao, Xi and Nie, Shaoheng and Wei, Yixuan and Xie, Zhenda and Chen, Ting and Zeng, Gang},
  year={2026}
}

```

## 4. 联系方式

如有问题，请提交 issue，或通过 [service@deepseek.com](mailto:service@deepseek.com) 联系。

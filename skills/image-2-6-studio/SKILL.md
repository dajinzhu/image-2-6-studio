---
name: image-2-6-studio
description: Generate or edit product photos, advertising images, and other raster visuals in Codex using its built-in image tool, with an explicitly selected GPT Image 2.6 API route when requested. Use for product mockups, campaign visuals, reference-based edits, or image variants; do not use for editable vector diagrams or for writing marketplace listings.
---

# Image 2.6 Studio

Turn a visual brief into an actual image, inspect the result, and refine the requested details. Support product and advertising work as well as other raster image requests; do not expand a simple brief into an unrelated marketing project.

## Choose the execution route

- **Built-in first:** for ordinary generation or image editing, use the available Codex image-generation tool, following the installed system imagegen skill. This route does not require an API key. The current tool interface may not expose a model selector or model identity: describe the tool used, and name the model only when the environment provides verifiable evidence.
- **Explicit GPT Image 2.6 API:** if the user specifically wants a verifiable 2.6 model or selects API mode, consult [API mode](references/api-mode.md). Use the existing system imagegen CLI, not a new wrapper. Explain that an API key, access, network, and usage-based charges may apply before a live call. Never ask the user to paste a key into chat, reveal it, or silently change models.
- If the chosen tool is unavailable, say what is missing and provide the prepared prompt; do not imply that an image was generated.

## Gather the brief

Identify the subject, purpose, output orientation, desired appearance, and any supplied reference. Preserve concrete user constraints. When details are missing but nonessential, use restrained defaults and proceed; ask only when missing information blocks a useful result, such as a request to reproduce a real product without a reference.

For a product image, specify scene, subject and materials, camera/framing, lighting, intended use, exact text if any, and what must remain unchanged. Use only details that advance the request. Treat fictional samples as samples; never invent brands, real sales results, certifications, or product properties.

For reference-based edits:

1. Inspect each available input image and identify its role. The edit target, product reference, and style reference are different inputs.
2. State what to change and what to preserve: product shape, color, label, logo, lettering, proportions, and camera angle when relevant.
3. Generate the image, then visually compare it with the reference. Check readable text, packaging, object count, edges, shadows, and any extra or missing details. Correct meaningful errors through a targeted follow-up; do not claim pixel-perfect preservation.
4. If exact product lettering or branding cannot be retained reliably, disclose it and recommend adding the client's authorized artwork in an editing tool after generation.

For new images, inspect the generated result for subject fidelity, composition, text, and artifacts. Keep the selected output at the user-requested location; for project assets copy it into the project workspace without overwriting an existing file. Show the result and report its saved path. Give the final prompt when useful for reuse.

## Ready-to-use prompt pattern

~~~text
用途：[商品图 / 广告图 / 封面]
主体：[商品或场景；有参考图时说明每张图的用途]
画面：[背景、材质、构图、相机角度]
光线与风格：[具体描述]
保留：[形状、颜色、文字、Logo 等必须保持的内容]
文字：[需逐字出现的内容；没有则写“无文字”]
限制：[画幅、不能出现的元素、交付要求]
~~~

After generation, use a focused edit such as: “只调整背景为浅色石材和窗边自然光；商品形状、标签和视角保持不变。” Verify the actual output rather than assuming the model obeyed every constraint.

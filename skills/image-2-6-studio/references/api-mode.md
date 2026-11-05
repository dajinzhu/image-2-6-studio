# GPT Image 2.6 API mode

Use this route only when the user explicitly wants API/model control. It calls the imagegen CLI already included with Codex; it does not introduce another API program. Verify the CLI exists and that the installed version supports the requested arguments. For current model details see [OpenAI image prompting](https://developers.openai.com/api/docs/guides/image-prompting) and [image generation](https://developers.openai.com/api/docs/guides/image-generation).

A live request needs a configured OPENAI_API_KEY, an OpenAI project with model access, network access and a Python environment with the OpenAI SDK. Usage may incur charges. If a credential decision is needed, use the available openai-platform-api-key workflow. Never request that a key be pasted into chat, printed, or committed. A dry run checks the CLI payload without calling the API.

## Windows PowerShell

~~~powershell
$taskCodexRoot = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $env:USERPROFILE '.codex' }
$taskImageGen = Join-Path $taskCodexRoot 'skills/.system/imagegen/scripts/image_gen.py'
python $taskImageGen generate --model gpt-image-2.6-sunburst --quality high --size 1536x1024 --prompt "A fictional unbranded amber candle on a light studio background, blank label, no words" --out output/imagegen/candle.png --dry-run
~~~

Remove the final --dry-run only after the user has explicitly chosen a live API request and the key and billing are ready. The system imagegen CLI's own output and options govern the request.

Edit an existing reference after the user explicitly requests an API edit:

~~~powershell
python $taskImageGen edit --model gpt-image-2.6-sunburst --quality high --size 1536x1024 --image path/to/reference.png --prompt "Change only the background to soft morning light. Preserve the product shape, label, lid and camera angle." --out output/imagegen/candle-edited.png --dry-run
~~~

Replace the image path and prompt with the actual task. Do not reuse an output path that already exists.

## macOS and Linux

~~~bash
task_codex_root="$CODEX_HOME"
if [ -z "$task_codex_root" ]; then task_codex_root="$HOME/.codex"; fi
task_image_gen="$task_codex_root/skills/.system/imagegen/scripts/image_gen.py"
python "$task_image_gen" generate --model gpt-image-2.6-sunburst --quality high --size 1536x1024 --prompt "A fictional unbranded amber candle on a light studio background, blank label, no words" --out output/imagegen/candle.png --dry-run
~~~

Sunburst is oriented toward detail and editing precision; Flare is oriented toward faster iteration. Use the model the user chooses. Review the actual result; specifying a model does not guarantee exact rendering of product identity or text.

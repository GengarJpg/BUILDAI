# Minecraft AI Structure Generator

A small CLI tool that uses an AI model to generate Minecraft worldbuilding structures from a text prompt.

## What it does

- Accepts a build prompt like: `"a wizard tower with blue roof"`
- Calls an OpenAI model to generate a structured 3D block layout
- Exports the result to a `.mcfunction` file with `setblock` commands

You can run the generated function in-game with `/function` (after putting it in a datapack).

## Requirements

- Python 3.10+
- An OpenAI API key

## Install

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Configure

```bash
export OPENAI_API_KEY="your_key_here"
```

## Usage

```bash
python mc_structure_ai.py \
  --prompt "A medieval gatehouse with torches and battlements" \
  --size 21 18 21 \
  --origin 0 64 0 \
  --output gatehouse.mcfunction
```

### Options

- `--prompt`: Natural language build description.
- `--size X Y Z`: Bounding box for generated structure.
- `--origin X Y Z`: World coordinate where the structure begins.
- `--model`: OpenAI model name (default: `gpt-4.1-mini`).
- `--temperature`: Creative variation (default: `0.7`).
- `--output`: Output `.mcfunction` path.

## Notes

- The tool uses `setblock` and does not clear existing terrain.
- It outputs one function; larger structures may take many commands.
- For survival-safe block lists, refine your prompt (e.g. "no command blocks").

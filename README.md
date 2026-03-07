# Claude Code Image Generator

A Claude Code plugin that generates images from text prompts using [NanoBanana Pro](https://www.nano-banana.com) via Chrome browser automation.

Claude Code doesn't have a built-in image generation feature. This plugin fills that gap by automating the NanoBanana Pro web interface through the Chrome browser extension.

## Requirements

- [Claude Code](https://claude.ai/claude-code) v1.0.33+
- [Claude in Chrome](https://claude.ai/chrome) browser extension
- [NanoBanana Pro](https://www.nano-banana.com) account (logged in via Chrome)

## Installation

```bash
claude /plugin install github:aliksir/claude-code-image-generator
```

Or for local development:

```bash
claude --plugin-dir ./claude-code-image-generator
```

## Usage

```
/image-generator:generate A cat wearing a space helmet floating through a galaxy
```

### Options

| Option | Values | Default | Description |
|--------|--------|---------|-------------|
| `--ratio` | auto, 1:1, 2:3, 3:4, 4:5, 9:16, 16:9, 3:2, 4:3, 5:4, 21:9 | auto | Aspect ratio |
| `--format` | JPEG, PNG | JPEG | Output format |
| `--resolution` | 1K, 2K, 4K | 1K | Image resolution |

### Examples

```
/image-generator:generate A minimalist logo for a tech startup --ratio 1:1 --format PNG

/image-generator:generate Panoramic mountain landscape at sunset --ratio 21:9 --resolution 4K
```

## How It Works

1. Opens NanoBanana Pro in Chrome via the claude-in-chrome extension
2. Enters your text prompt and selected options
3. Clicks "Generate" and waits for the result
4. Reports back with a screenshot of the generated image, task ID, and remaining credits

## Cost

Each generation costs **20 NanoBanana credits**. Credit balance is reported after each generation.

## Limitations

- Requires Chrome browser with the claude-in-chrome extension running
- Requires an active NanoBanana Pro account and login session
- Generation takes ~30 seconds
- Browser UI changes on nano-banana.com may require plugin updates

## License

MIT

---

# Claude Code Image Generator (Japanese)

Claude Codeのテキストプロンプトから画像を生成するプラグイン。[NanoBanana Pro](https://www.nano-banana.com) をChrome自動化で操作します。

## 必要条件

- [Claude Code](https://claude.ai/claude-code) v1.0.33+
- [Claude in Chrome](https://claude.ai/chrome) ブラウザ拡張
- [NanoBanana Pro](https://www.nano-banana.com) アカウント（Chromeでログイン済み）

## インストール

```bash
claude /plugin install github:aliksir/claude-code-image-generator
```

## 使い方

```
/image-generator:generate 宇宙ヘルメットをかぶった猫が銀河を漂っている
```

### オプション

| オプション | 値 | デフォルト | 説明 |
|-----------|-----|----------|------|
| `--ratio` | auto, 1:1, 2:3, 3:4, 4:5, 9:16, 16:9, 3:2, 4:3, 5:4, 21:9 | auto | アスペクト比 |
| `--format` | JPEG, PNG | JPEG | 出力形式 |
| `--resolution` | 1K, 2K, 4K | 1K | 解像度 |

## コスト

1回の生成で **20クレジット** 消費。生成後にクレジット残高が報告されます。

## ライセンス

MIT

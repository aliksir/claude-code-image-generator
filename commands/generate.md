# Generate Image from Text Prompt

Generate an image using NanoBanana Pro via browser automation (browser-cli).

## Arguments

$ARGUMENTS contains the text prompt. Optional parameters:
- `--ratio <value>`: Aspect ratio (auto, 1:1, 2:3, 3:4, 4:5, 9:16, 16:9, 3:2, 4:3, 5:4, 21:9) Default: auto
- `--format <value>`: Output format (JPEG, PNG) Default: JPEG
- `--resolution <value>`: Resolution (1K, 2K, 4K) Default: 1K

## Prerequisites

- [browser-cli](https://github.com/user/browser-cli) installed and available in PATH
- NanoBanana Pro account (https://www.nano-banana.com)
- Logged in to NanoBanana Pro in the browser

## Steps

### 1. Browser Setup

1. Run `browser-cli snapshot` to check the current session state
   - If no session exists, run `browser-cli open --headed` to launch the browser
2. Check if the NanoBanana Pro generator page is open (check the URL in the snapshot output)
   - If not, run `browser-cli goto "https://www.nano-banana.com/ja/nanobananapro#generator"`
3. Run `browser-cli snapshot` to check the page state
4. Verify login status (check if "Generate" button and credit balance are visible)
   - If not logged in, report "Login required. Please log in to NanoBanana Pro in the browser window." and abort

### 2. Mode Check

**Important**: Verify the "Text to Image" tab is selected.
- If "Image Edit" tab is selected, click the "Text to Image" button using `browser-cli click <ref>` to switch
- "Image Edit" mode requires an image upload and cannot generate from text alone

### 3. Enter Prompt

1. Find the prompt textbox ref from the snapshot (placeholder contains text about describing an image)
2. Use `browser-cli fill <ref> "<prompt text>"` to enter the prompt from $ARGUMENTS (max 10000 characters)

### 4. Set Options (if specified)

1. Aspect ratio: Click the corresponding button ref using `browser-cli click <ref>` (default: auto)
2. Output format: Click JPEG or PNG button (default: JPEG)
3. Resolution: Click 1K / 2K / 4K button (default: 1K)

### 5. Generate

1. Click the "Generate" button using `browser-cli click <ref>`
2. Run `browser-cli snapshot` at 10-second intervals to wait for completion (max 90 seconds)
3. Generation is complete when the image appears in the result area

### 6. Report Results

1. Run `browser-cli screenshot` to capture the generated image
2. Record the task ID (if displayed on the page)
3. Check remaining credits (read "Credits available: N" from the snapshot)
4. Report to the user:
   - Screenshot of the generated image (file path)
   - Credits consumed: 20
   - Remaining credits (read from snapshot)
   - Task ID (if available)

## Notes

- Each generation costs 20 credits
- Generation takes approximately 30-60 seconds
- Browser must be launched with `--headed` flag so the user can log in if needed
- If the login session has expired, ask the user to log in again
- The page may display in English or Japanese — button names work in either language
- To download the image, use the download button in the result area or right-click and save

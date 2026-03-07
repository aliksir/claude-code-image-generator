# Generate Image from Text Prompt

Generate an image using NanoBanana Pro via Chrome browser automation.

## Arguments

$ARGUMENTS contains the text prompt. Optional parameters:
- `--ratio <value>`: Aspect ratio (auto, 1:1, 2:3, 3:4, 4:5, 9:16, 16:9, 3:2, 4:3, 5:4, 21:9) Default: auto
- `--format <value>`: Output format (JPEG, PNG) Default: JPEG
- `--resolution <value>`: Resolution (1K, 2K, 4K) Default: 1K

## Prerequisites

- Claude Code with Chrome browser automation (claude-in-chrome extension)
- NanoBanana Pro account (https://www.nano-banana.com)
- Logged in to NanoBanana Pro in Chrome

## Steps

### 1. Browser Setup

1. Call `tabs_context_mcp` to check current tabs
2. Check if NanoBanana Pro generator page is open
   - If not, call `tabs_create_mcp` then `navigate` to `https://www.nano-banana.com/ja/nanobananapro#generator`
3. Call `read_page` (filter: interactive) to check the page state
4. Verify login status (check if "Generate" button is visible)
   - If not logged in, report "Login required. Please log in to NanoBanana Pro in your browser." and abort

### 2. Mode Check

**Important**: Verify the "Text to Image" tab is selected.
- If "Image Edit" tab is selected, click the "Text to Image" button to switch
- "Image Edit" mode requires an image upload and cannot generate from text alone

### 3. Enter Prompt

1. Find the prompt textbox (placeholder contains text about describing an image)
2. Use `form_input` to enter the prompt text from $ARGUMENTS (max 10000 characters)

### 4. Set Options (if specified)

1. Aspect ratio: Click the corresponding button (default: auto)
2. Output format: Click JPEG or PNG button (default: JPEG)
3. Resolution: Click 1K / 2K / 4K button (default: 1K)

### 5. Generate

1. Scroll to make the "Generate" button visible
2. Click the "Generate" button
3. Confirm the button changes to a loading state and the result area shows a waiting indicator
4. Take screenshots at 10-second intervals to wait for completion (max 60 seconds)
5. Generation is complete when the image appears in the result area

### 6. Report Results

1. Take a screenshot of the generated image
2. Record the task ID (displayed at the bottom of the page)
3. Check remaining credits
4. Report to the user:
   - Screenshot of the generated image
   - Credits consumed: 20
   - Remaining credits (read from page)
   - Task ID

## Notes

- Each generation costs 20 credits
- Generation takes approximately 30 seconds
- If the login session has expired, ask the user to log in again
- To download the image, use the download button in the result area or right-click and save

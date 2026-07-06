# Challenge 04: Neo Sees The Code

This challenge features a Matrix-style video with falling green characters representing Morse code.

## Challenge Description

"This is it. Neo finally sees the Matrix - not as reality, but as pure code. The transmission from the machines isn't noise anymore, it's a language. Green characters cascade down like rain, each one carrying meaning. When Neo could finally read the Matrix code, he became The One. Can you decode the pattern hidden in the falling letters?"

## How to Solve

1. **Watch the video**: You'll see green Chinese characters falling from top to bottom on a black background, just like the Matrix code. Each complete letter (all its dots and dashes) falls together as a horizontal group with 10 characters per line.

2. **Understand the encoding**:
   - **'点' (diǎn - "dot")** = dot (.) in Morse code - bright green
   - **'线' (xiàn - "line")** = dash (-) in Morse code - bright green
   - **'{'** and **'}'** = Unchanged punctuation marks - bright green
   - **Filler characters** (faded green) = background Matrix rain effect, ignore these:
     - '雨' (yǔ - "rain")
     - '绿' (lǜ - "green")
     - '码' (mǎ - "code")
     - '数' (shù - "number/digital")
     - '字' (zì - "character/word")
   - Each line of bright green symbols (ignore faded ones) represents ONE Morse character
   - The morse symbols are padded with faded filler characters

3. **Record the sequence**: As you watch, write down each line of bright green characters:
   - Example: You see `点点点点` (4 bright dots) falling together, then `线点线点` (dash-dot-dash-dot), then `{`, etc.
   - Ignore the faded characters - they're just background decoration

4. **Convert to Morse**: Replace '点' with '.' and '线' with '-' for each line:
   - `点点点点` → `....` (H)
   - `线点线点` → `-.-.` (C)
   - `{` → `{`
   - etc.

5. **Decode to text**: Use a Morse code chart to convert each pattern to its letter

## Solution Methods

### Method 1: Manual Observation (Recommended)

Watch the video and note down the sequence manually:

```bash
python solve_video_simple.py --manual
```

Then input the sequence you observed when prompted.

### Method 2: Automatic OCR (Advanced)

Requires pytesseract and tesseract-ocr:

```bash
# Install dependencies
pip install pytesseract
brew install tesseract  # On macOS
# sudo apt-get install tesseract-ocr  # On Linux

# Run solver
python solve_video_simple.py output.mp4
```

### Method 3: Frame-by-Frame Analysis

You can also step through the video frame-by-frame using any video player and record each character as it appears.

## Generating the Challenge

To generate a new video with custom text:

```bash
python generate_video.py "YOUR TEXT HERE"
```

This creates `output.mp4` with your text encoded in falling Matrix-style Chinese characters.

To add music to the video:

```bash
python generate_video.py "YOUR TEXT HERE" path/to/music.mp3
```

This creates both `output.mp4` and `output_with_music.mp4` with the audio track combined.

## Key Concepts

- **Morse Code**: International encoding system where each letter/number has a unique pattern of dots and dashes
- **Matrix Visual Style**: Green text on black background, characters falling from top
- **Pattern Recognition**: Identifying and recording visual patterns
- **Decoding**: Converting symbolic patterns back to readable text

## Morse Code Reference

```
A .-    B -...  C -.-.  D -..   E .     F ..-.
G --.   H ....  I ..    J .---  K -.-   L .-..
M --    N -.    O ---   P .--.  Q --.-  R .-.
S ...   T -     U ..-   V ...-  W .--   X -..-
Y -.--  Z --..

0 ----- 1 .---- 2 ..--- 3 ...-- 4 ....-
5 ..... 6 -.... 7 --... 8 ---.. 9 ----.
```

## Tips

- Each line of characters falls continuously from top to bottom at constant speed (100 px/s)
- All symbols for one Morse character move together as a horizontal group (10 characters per line)
- Lines are flush to the left side of the screen
- **Bright green characters ('点', '线', '{', '}', '_')** are the Morse code - write these down!
- **Faded dark green characters** ('雨', '绿', '码', '数', '字') are just background Matrix rain effect - ignore them
- The color difference makes it easy to distinguish Morse symbols from decoration
- Watch the video multiple times if needed - there's no time limit!
- You can pause the video at any point to record what you see
- The video starts with a black screen and continues for 5.5 seconds after the last line enters the screen

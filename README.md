# Target Image Detection Auto Clicker

A desktop utility that searches a selected screen area for one or more target images, then moves the mouse to the center of the best-matching image and clicks it.

This project is designed for personal automation practice, UI testing, repetitive local workflows, and controlled environments where image-based mouse automation is allowed.

<img width="653" height="645" alt="螢幕擷取畫面 2026-05-03 034414" src="https://github.com/user-attachments/assets/7f849c73-5233-4696-8f04-be6fbba2ac6e" />


## Overview

Target Image Detection Auto Clicker lets you:

- Load one image or an entire folder of target images.
- Search a custom screen area for matching images.
- Click the center of the detected target image.
- Use similarity thresholds to control matching strictness.
- Use hotkeys to set the detection area quickly.
- Run quickly by limiting the scan area and number of templates.
- Keep the window always on top.
- Run without a CMD window by using the `.pyw` file extension.
- Switch the interface between multiple languages if your version includes the language menu.

## Features

- Template-image detection using OpenCV.
- Folder-based image loading.
- Supports multiple image formats.
- Supports Chinese and Unicode file paths.
- Clicks the center of the detected target.
- Adjustable similarity threshold.
- Adjustable click delay.
- Custom detection area.
- Full-screen detection option.
- Global hotkeys.
- Emergency stop.
- Always-on-top window support.
- Optional multilingual interface.

## Supported Image Formats

```text
.png
.jpg
.jpeg
.bmp
.webp
```

## Supported Interface Languages

If you are using the multilingual version, the interface can support:

- Traditional Chinese
- Simplified Chinese
- English
- Japanese
- Korean
- French
- Spanish
- German
- Portuguese
- Russian

## How It Works

The program captures a selected area of the screen and compares it against one or more target images using OpenCV template matching.

For each target image, it calculates a similarity score.

If the best score is higher than the configured threshold, the program clicks the center of that matched image.

Example:

```text
Target image: target.png
Similarity threshold: 0.75
Detection area: X=400, Y=200, W=1000, H=600
```

If the target appears inside that area and its similarity score is at least `0.75`, the program clicks its center.

## Requirements

### Python

Recommended:

```text
Python 3.10 or newer
```

During installation on Windows, enable:

```text
Add python.exe to PATH
```

### Python Packages

Install the required packages:

```bash
python -m pip install opencv-python numpy pyautogui pillow keyboard
```

## Files

Recommended repository structure:

```text
TargetImageAutoClicker/
├── TargetClicker.py
├── TargetClicker.pyw
├── README.md
└── targets/
    ├── target_1.png
    ├── target_2.png
    └── target_3.png
```

Notes:

- `TargetClicker.py` is useful for debugging because it can show CMD error messages.
- `TargetClicker.pyw` is useful for normal use because it opens without a CMD window.
- The `targets` folder should contain the images you want the program to search for.

## Usage

### 1. Start the Program

For debugging:

```bash
python TargetClicker.py
```

For normal use without a CMD window:

```text
Double-click TargetClicker.pyw
```

### 2. Prepare Target Images

Create a folder such as:

```text
targets
```

Place your target images inside it:

```text
targets/target_1.png
targets/target_2.png
targets/target_3.png
```

For best results:

- Crop the target image tightly.
- Avoid including too much background.
- Use clear images with stable size and appearance.
- Keep the target image close to the same size as it appears on screen.

### 3. Select the Target Image Folder

Click:

```text
Select folder
```

Then choose the folder that contains your target images.

The program will load all supported image files in that folder.

### 4. Set the Detection Area

You can set a custom screen detection area with `F7`.

1. Move your mouse to the top-left corner of the desired detection area.
2. Press `F7`.
3. Move your mouse to the bottom-right corner of the desired detection area.
4. Press `F7` again.

The program automatically fills:

```text
X / Y / W / H
```

You can also use the detection-area button if your version includes one.

### 5. Use Full-Screen Detection

Click:

```text
Full screen
```

This sets the detection area to the entire screen.

For better speed, use a smaller detection area whenever possible.

### 6. Start Detection and Clicking

Click:

```text
Start
```

The program will scan the selected screen area, find the best-matching target image, and click its center if the similarity score is high enough.

### 7. Stop Detection

Press:

```text
F8
```

or click:

```text
Stop
```

You can also move the mouse to the top-left corner of the screen to trigger PyAutoGUI's fail-safe stop.

## Hotkeys

| Hotkey | Action |
|---|---|
| `F7` | Set detection area: first press = top-left, second press = bottom-right |
| `F8` | Emergency stop |

Some versions may include additional hotkeys, depending on your implementation.

## Settings

### Similarity Threshold

Controls how closely the screen image must match the target image.

Recommended values:

```text
0.65 = loose matching
0.75 = normal matching
0.85 = strict matching
0.90 = very strict matching
```

If the program cannot find the target:

```text
Lower the threshold
```

If the program clicks the wrong target:

```text
Raise the threshold
```

### Click Delay

Controls the delay after each click.

Recommended values:

```text
0 = fastest
0.05 = very fast
0.15 = safer and easier to observe
0.3 = slow and controlled
```

### Detection Area

The detection area is defined by:

```text
X = left coordinate
Y = top coordinate
W = width
H = height
```

Example:

```text
X=400
Y=200
W=1000
H=600
```

This means the program scans a rectangle starting at `(400, 200)` with width `1000` and height `600`.

## Performance Tips

- Use the smallest detection area possible.
- Avoid full-screen detection when speed matters.
- Keep the number of target images low.
- Use tightly cropped target images.
- Use images with the same size as they appear on screen.
- Set click delay to `0` for maximum speed.
- Avoid scanning high-resolution full-screen areas unless necessary.

## Image Preparation Tips

For best matching results:

- Crop the image to the exact target.
- Avoid transparent shadows or large background areas.
- Avoid scaling differences between the target image and the on-screen image.
- Avoid screenshots with blur or compression artifacts.
- Use PNG when possible.
- If the target changes size, prepare multiple versions at different sizes.

Example:

```text
Good:
A tightly cropped target icon.

Bad:
A full screenshot containing the target somewhere inside.
```

## Important Notes

- The program detects images, not semantic objects.
- The target image must visually match what appears on screen.
- If the target changes size, color, rotation, or style, detection accuracy may drop.
- If multiple similar targets exist, the program may click the one with the highest similarity.
- Recreate the target image if the UI theme, resolution, or scaling changes.
- Use this only in environments where automation is allowed.
- Do not use this tool for bypassing CAPTCHA, login verification, anti-bot systems, or security mechanisms.
- Some games or protected applications may block simulated mouse input.
- The `keyboard` package may require administrator privileges on some Windows systems for global hotkeys to work.

## Troubleshooting

### The Program Does Not Open

Run the `.py` version from CMD:

```bash
python TargetClicker.py
```

Then read the error message.

### The CMD Window Appears

Rename the file extension:

```text
.py -> .pyw
```

Example:

```text
TargetClicker.pyw
```

### Hotkeys Do Not Work

Try running CMD as administrator:

```text
Start Menu -> CMD -> Right click -> Run as administrator
```

Then run:

```bash
python TargetClicker.py
```

### The Program Cannot Read the Image

If your image path contains Chinese or special characters, use a Unicode-safe image loader in your Python code.

A common OpenCV issue is:

```text
cv2.imread() cannot read Unicode paths correctly on some Windows systems
```

Recommended fix:

```python
data = np.fromfile(path, dtype=np.uint8)
img = cv2.imdecode(data, cv2.IMREAD_COLOR)
```

### The Program Cannot Find the Target

Try these fixes:

```text
Lower the similarity threshold
Use a smaller and more accurate target image
Make sure the target is visible inside the detection area
Use the same image size as the on-screen target
Reduce Windows display scaling differences
```

### The Program Clicks the Wrong Place

Try these fixes:

```text
Raise the similarity threshold
Use a more unique target image
Crop the template more tightly
Reduce the detection area
Remove similar-looking target images from the folder
```

### The Program Is Too Slow

Try:

```text
Use a smaller detection area
Reduce the number of target images
Set click delay to 0
Use smaller target images
Avoid full-screen detection
```

### The Program Clicks Too Fast

Increase click delay:

```text
0.05
0.15
0.3
```

### The Program Freezes or Keeps Clicking

Press:

```text
F8
```

or move the mouse to the top-left corner of the screen.

## Safety

This program can move and click your mouse automatically.

Before starting:

- Confirm the detection area.
- Test with a slower click delay first.
- Keep `F8` ready for emergency stop.
- Keep PyAutoGUI fail-safe enabled.
- Avoid using it on important windows until you have tested the settings.

## License

You may publish this project under the MIT License if you want it to be open source.

## Disclaimer

This project is intended for educational, personal, and authorized automation use only. The author is not responsible for misuse, violations of third-party terms of service, or automation in restricted environments.

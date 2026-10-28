# scorpion

Displays the metadata of image files: basic file attributes and EXIF data.
Second program of **Arachnida** (42 Cybersecurity Piscine): it analyzes the images downloaded by [`spider`](../spider/).

## Usage

```
./scorpion FILE1 [FILE2 ...]
```

Supported formats: JPEG (`.jpg`, `.jpeg`), PNG, GIF and BMP.

## Output

For each file:

- **Basic attributes**: name, size, format, dimensions, and dates (creation when available, last modification).
- **EXIF data**: camera, software, shooting date, GPS position… or a notice that the file has none.
- **Other metadata** when present, such as PNG text chunks and JPEG/GIF comments.

A missing, unreadable or corrupt file is reported, then the next file is processed.

## Why it matters

Metadata is "data about data". A photo posted online can reveal the camera and software used, when it was taken and even where.

## Requirements

Python 3.10 or later, standard library only. The metadata parsing is written by hand (JPEG segments → TIFF header → IFDs, PNG chunks).

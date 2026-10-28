# Arachnida

Introductory project to **web scraping and metadata** (42 Cybersecurity Piscine).

Metadata is "data about data": the images we publish can reveal who created them, with which device, when and where. This project collects images from the web, then reads what their metadata gives away.

## Programs

| Program | Role | Usage |
|---|---|---|
| [`spider`](spider/) | Downloads the images of a website, optionally following its links recursively | `./spider [-r [-l N]] [-p PATH] URL` |
| [`scorpion`](scorpion/) | Displays the metadata of image files: basic attributes and EXIF data | `./scorpion FILE1 [FILE2 ...]` |

Both handle `.jpg` / `.jpeg`, `.png`, `.gif` and `.bmp`. Each folder has its own README with the details.

## Quick start

```
cd spider
./spider https://books.toscrape.com/          # images saved in ./data/
cd ../scorpion
./scorpion ../spider/data/*.jpg               # show their metadata
```

## Layout

```
arachnida/
├── spider/      spider program + README
└── scorpion/    scorpion program + README
```

## Requirements

Python 3.10 or later, standard library only: nothing to install, nothing to compile.
All the logic is our own: no `wget`, no `scrapy`, no metadata library.

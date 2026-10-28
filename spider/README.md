# spider

Downloads the images of a website, optionally following its links recursively.
First program of **Arachnida** (42 Cybersecurity Piscine): the images it saves can then be analyzed with [`scorpion`](../scorpion/).

## Usage

```
./spider [-r [-l N]] [-p PATH] URL
```

| Option    | Effect                                                                  | Default   |
|-----------|-------------------------------------------------------------------------|-----------|
| `-r`      | Recursively download the images of `URL` and of the pages it links to   | off       |
| `-l N`    | Maximum depth of the recursion (only with `-r`)                         | `5`       |
| `-p PATH` | Directory where the images are saved (created if missing)               | `./data/` |

Downloaded extensions: `.jpg` / `.jpeg`, `.png`, `.gif`, `.bmp`.

## Examples

```
./spider https://example.com                  # images of this page only
./spider -r https://example.com               # follow links up to depth 5
./spider -rl 2 -p ./images https://example.com
```

## Behaviour

- Without `-r`, only the images of the given page are downloaded. `-l` without `-r` is a usage error.
- With `-r`, the start page is depth 0 and links are followed up to depth `N`. Pages outside the start host are not crawled.
- Errors (invalid URL, unreachable host, HTTP error, timeout) are reported and skipped: the program never stops with a traceback.

## Requirements

Python 3.10 or later, standard library only (nothing to install). The crawling logic is our own: no `wget`, no `scrapy`.

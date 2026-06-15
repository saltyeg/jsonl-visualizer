# JSONL Visualizer

A lightweight browser-based viewer for JSONL and NDJSON files. Open a newline-delimited JSON file, browse each row, filter across the file, and inspect parsed JSON alongside readable message content.

## Features

- Open `.jsonl`, `.ndjson`, JSON, or plain text files from your browser
- Drag and drop files onto the app
- Filter rows by raw JSON, line number, field names, or parse errors
- View each row as formatted JSON
- Highlight invalid JSON lines with the parser error
- Render common content fields as readable Markdown
- Summarize top-level object fields for quick scanning
- Runs entirely in the browser with no upload step

## Usage

Open `index.html` in a browser, then choose **Open .jsonl** or drag a file onto the page.

Each non-empty line is parsed as one JSON value. Valid rows show a field summary and formatted JSON. Invalid rows remain visible so you can find and fix malformed lines.

The app looks for readable text in these fields:

- `content`
- `message.content`
- `attachment.content`

When one of those fields contains text, it is rendered above the raw JSON view.

## Local Development

This project is a single static HTML file with embedded CSS and JavaScript.

```sh
open index.html
```

You can also serve the folder locally if your browser or workflow prefers an HTTP origin:

```sh
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## File Format

Input files should contain one JSON value per line:

```jsonl
{"role":"user","content":"Hello"}
{"role":"assistant","content":"Hi there."}
```

Blank lines are ignored.

## Privacy

Files are read locally through the browser `FileReader` API. The app does not send file contents to a server.

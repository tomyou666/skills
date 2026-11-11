---
name: drawio-reproduce
description: Recreates an architecture or flow diagram as draw.io XML and opens it with the draw.io MCP. Use when the user asks to reproduce, redraw, copy, or trace a figure into draw.io or a .drawio file, including when they supply icons. Adds the draw.io MCP server when its tools are absent.
disable-model-invocation: true
---

# Reproduce a diagram

The image is the spec. Copy its labels, boxes, and connections. Change only what the user explicitly changed.

Default fidelity is structure. Match zones, labels, and arrow direction. Do not match pixel spacing, arrow bends, or exact colors. Colors only need to separate zones.

Labels and edge labels use `fontFamily=Meiryo` and `fontSize=24`. Size the cell for that type: at least 36px tall per line, and wide enough that the words are not clipped. A short role caption needs about 220px of width. Offset an edge label off the stroke so the text does not sit on the line. Wrap a long edge label onto two lines.

A symbol that must be recognized, such as a person or a lock, is at least 96px square.

## Icons

Do not embed PNG files. When the user supplies icons, draw a labeled placeholder and tell them which file to drop onto it. When the user does not supply icons, search the draw.io MCP with `search_shapes` and use the matching built-in shape.

## MCP

If the draw.io tools are absent, merge this into the project's `.cursor/mcp.json` under `mcpServers`. Keep every other server. Create the file when it is missing.

```json
"drawio": {
  "command": "npx",
  "args": ["-y", "@drawio/mcp"]
}
```

Reload MCP servers, then continue.

## Steps

1. Read the image once.
2. Decide the placement yourself. Do not hand it to auto-layout. Edges are orthogonal and connect center to center. The result is one `mxGraphModel`. A short script may emit that XML and nothing else.
3. Pass that XML to `open_drawio_xml` with `dark` false. That call is the edit. When a project file is required, write the same XML into an uncompressed `.drawio`.
4. Do not open a browser, take a screenshot, or start a second process to open the diagram. The user checks the result.

## draw.io

- Do not set `postLayout` `elk` on a hand-placed diagram.
- Do not set `routing` `libavoid` when large background containers exist. Edges route around them.
- Do not set `exitX`, `entryX`, or waypoints.
- Put real `<br>` and `<b>` in cell values and let the XML serializer escape them once.
- Use `shape=cloud` for a cloud outline.
- An edge's parent is the innermost container that holds both ends. Otherwise parent `1`.

## Done

Give the user the `.drawio` path when you wrote one. Name each placeholder and the file that belongs on it.

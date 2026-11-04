# Execution Lock

> Machine-readable execution contract. Executor MUST `read_file` this before every SVG page.

## canvas
- viewBox: 0 0 1280 720
- format: PPT 16:9

## colors
- bg: #FFFFFF
- secondary_bg: #F5F7FA
- primary: #1565C0
- accent: #FF6F00
- secondary_accent: #1E88E5
- text: #1D1D1F
- text_secondary: #6B7280
- text_tertiary: #9CA3AF
- border: #E5E7EB
- success: #2E7D32
- warning: #C62828

## typography
- title_family: Georgia, "Microsoft YaHei", "PingFang SC", serif
- body_family: "Microsoft YaHei", "PingFang SC", Arial, sans-serif
- emphasis_family: Georgia, "Microsoft YaHei", serif
- code_family: Consolas, "Courier New", monospace
- body: 18
- title: 30
- subtitle: 24
- annotation: 14
- cover_title: 60

## icons
- library: tabler-outline
- stroke_width: 2
- brand_library: simple-icons
- inventory: network, robot, users, shield-check, database, bolt, chart-bar, layers-intersect, lock, checklist, message-2, clock, target, server, puzzle, hierarchy, alert-triangle, bulb, cloud, list-check, brain, git-branch

## page_rhythm
- P01: anchor
- P02: dense
- P03: breathing
- P04: dense
- P05: anchor
- P06: breathing
- P07: dense
- P08: dense
- P09: dense
- P10: dense
- P11: breathing
- P12: dense
- P13: dense
- P14: anchor

## page_charts
- P05: layered_architecture
- P06: hub_spoke
- P11: numbered_steps
- P12: basic_table

## forbidden
- Mixing icon libraries
- rgba()
- `<style>`, `class`, `<foreignObject>`, `textPath`, `@font-face`, `<animate*>`, `<script>`, `<iframe>`, `<symbol>`+`<use>`
- `<g opacity>` (set opacity on each child element individually)
- HTML named entities in text — write as raw Unicode; XML reserved chars escaped as &amp; &lt; &gt; &quot; &apos;

# Anthropic Academy AI glossary

Unofficial study notes on Anthropic Academy courses (the Claude Certification, Developer Foundation): one
glossary and one set of mind maps per course. Not affiliated with or endorsed by Anthropic.

- Each term is the course's own English word, defined in a short paragraph summarized from the course,
  with its French translation in parentheses. Every French term was checked against French AI and
  computing sources (vendor docs, official terminology, research), not taken from a dictionary.
- The entries link to each other, and each one points to the mind map that shows it.

## Courses

| Course                                                  | Glossary                                                | Mind maps                                                    |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| 01 — AI Capabilities and Limitations (and its PDF annex) | [index.md](01-ai-capabilities-and-limitations/index.md) | [mindmap.md](01-ai-capabilities-and-limitations/mindmap.md) |
| 02 — AI Fluency for Builders                             | [index.md](02-ai-fluency-for-builders/index.md)         | [mindmap.md](02-ai-fluency-for-builders/mindmap.md)         |

Each course folder stands alone, so that one course can be revised without the others: a term two
courses define has an entry in each (the same text, or this course's own definition), and a mind map
is copied rather than linked.

## Layout of a course folder

```
<course>/
  index.md     the glossary: one ### heading per term, « English term *(French term)* »
  mindmap.md   a table of contents, then each mind map with a caption
  mindmap/     <name>.puml (PlantUML source), <name>.png and <name>.svg (rendered)
```

After editing a `.puml`, render it again from `mindmap/`:

```bash
java -jar plantuml.jar -tpng <name>.puml && java -jar plantuml.jar -tsvg <name>.puml
```


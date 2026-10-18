# todoit-expert Wiki — Schema

## Page Types
- **Knowledge page**: Core domain content with frontmatter (tags, summary, plus any per-domain required fields)

## Conventions
- Filenames: kebab-case, descriptive
- Links: standard markdown (`[Page](page.md)`)
- Frontmatter: `tags` and `summary` required on all knowledge pages; additional required fields declared in this schema.md

## Tag Prefix

Every knowledge page's `tags:` value opens with this domain's prefix:

```yaml
tags: [todoit-expert/{subtopic}]
summary: "One-line description of the page"
```

## Evolution
Review and update this schema after every 10-20 ingests.

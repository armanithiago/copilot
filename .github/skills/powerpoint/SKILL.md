---
name: powerpoint
description: Create and manipulate Microsoft PowerPoint presentations (.pptx files). Use this skill when asked to create slides, presentations, pitch decks, or visual content with text, bullets, tables, and charts.
---

## Creating PowerPoint Presentations

When asked to create or manipulate PowerPoint presentations, follow these steps:

### 1. Understand the Presentation Goal

Ask clarifying questions:
- What is the presentation purpose (pitch, report, training, proposal)?
- Who is the audience?
- How many slides are needed?
- What data or content should be visualized?
- Are there specific formatting or branding requirements?

### 2. Structure the Presentation

Break the presentation into logical sections:

**Typical structure**:
- Title slide: Presentation title, author, date
- Overview/Agenda: What the presentation covers
- Content slides: Main points, data, analysis
- Summary/Conclusion: Key takeaways
- Call to action or next steps

**Slide types**:
- **Title slides**: Main presentation title and subtitle
- **Content slides**: Title with bullet points or text
- **Section slides**: Section headers to break up presentation
- **Data slides**: Tables, charts, or visual data
- **Blank slides**: Custom content or images

### 3. Create the Presentation

Use the PowerPoint tool with JSON structure:

**Basic structure**:
```json
{
  "title": "Presentation Title",
  "author": "Your Name",
  "slides": [
    {
      "type": "title",
      "title": "Main Title",
      "subtitle": "Subtitle Text"
    },
    {
      "type": "content",
      "title": "Slide Title",
      "content": ["Bullet point 1", "Bullet point 2", "Bullet point 3"]
    },
    {
      "type": "section",
      "title": "Section Header"
    }
  ]
}
```

### 4. Add Content

For each slide, determine:
- **Title**: Clear, descriptive slide title
- **Content type**: Bullets, text, table, chart, or image
- **Formatting**: Font size, colors, alignment

**Bullet point slides**:
```json
{
  "type": "content",
  "title": "Key Points",
  "content": [
    "First key point",
    "Second key point",
    "Third key point"
  ]
}
```

**Table slides**:
```json
{
  "type": "table",
  "title": "Comparison Table",
  "headers": ["Feature", "Option A", "Option B"],
  "rows": [
    ["Cost", "Low", "High"],
    ["Speed", "Medium", "Fast"],
    ["Quality", "Good", "Excellent"]
  ]
}
```

**Chart slides**:
```json
{
  "type": "chart",
  "title": "Sales Trend",
  "chartType": "line",
  "labels": ["Q1", "Q2", "Q3", "Q4"],
  "data": [100, 150, 120, 200]
}
```

### 5. Verify Content

Before finalizing:
- [ ] Does each slide have clear, concise content?
- [ ] Is the flow logical and easy to follow?
- [ ] Are bullet points scannable (not paragraphs)?
- [ ] Do titles accurately describe slide content?
- [ ] Is the data accurate and well-formatted?
- [ ] Are visuals (tables, charts) clear and labeled?

### 6. Generate the File

Create the PowerPoint file at the requested location:

```bash
ts-node src/tools/powerpoint-tool.ts create "/path/to/presentation.pptx" '<json-structure>'
```

Or use outline format for quick creation:

```bash
ts-node src/tools/powerpoint-tool.ts outline "/path/to/presentation.pptx" '<json-structure>'
```

### 7. Clean temporary files

Delete every file created to execute this skill, leave only the .pptx file in place.

## Outline Format (Quick Method)

For faster presentation creation without full JSON:

```json
{
  "title": "Presentation Title",
  "slides": [
    {
      "title": "Slide 1 Title",
      "points": ["Point 1", "Point 2", "Point 3"]
    },
    {
      "title": "Slide 2 Title",
      "points": ["Point A", "Point B"]
    }
  ]
}
```

## Capabilities

**Text and Formatting**:
- Titles and subtitles
- Bullet points and text blocks
- Custom fonts and colors
- Text alignment and sizing

**Tables**:
- Headers and data rows
- Custom column widths
- Formatted cells

**Charts**:
- Bar charts
- Line charts
- Pie charts
- Custom labels and data

**Images**:
- Insert images at specific positions
- Resize and position on slides
- Support for common image formats

**Layouts**:
- Title slide layout
- Content with bullets
- Section headers
- Blank slides for custom content

## Common Presentation Types

**Pitch Deck**:
- Problem/opportunity
- Solution
- Market/audience
- Differentiation
- Financial projections
- Call to action

**Status Report**:
- Executive summary
- Key metrics
- Accomplishments
- Challenges/risks
- Next steps
- Questions/discussion

**Training Presentation**:
- Learning objectives
- Content modules
- Examples and case studies
- Practice/exercises
- Key takeaways
- Resources

**Proposal Presentation**:
- Executive summary
- Problem statement
- Proposed solution
- Timeline and milestones
- Budget/investment
- Next steps

## Tips for Effective Presentations

- **One idea per slide**: Focus each slide on a single concept
- **Scannable content**: Use bullet points, not paragraphs
- **Data visualization**: Use charts instead of tables when possible
- **Consistent formatting**: Same fonts, colors, alignment throughout
- **Visual hierarchy**: Use sizes and colors to guide attention
- **Clean layout**: Leave whitespace, don't overcrowd slides

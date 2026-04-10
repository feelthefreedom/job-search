# Spreadsheet Styling — openpyxl

Apply to every new row. Never restyle existing rows.

## URL (column 7)

```python
cell.hyperlink = url
cell.font = Font(color="0563C1", underline="single")
```

## Match Score (column 13)

| Range | Fill | Font |
|-------|------|------|
| ≥ 70 | `PatternFill(start_color="C6EFCE", fill_type="solid")` | `Font(color="006100")` |
| 50–69 | `PatternFill(start_color="FFEB9C", fill_type="solid")` | `Font(color="9C6500")` |
| < 50 | `PatternFill(start_color="FFC7CE", fill_type="solid")` | `Font(color="9C0006")` |

## Details Status (column 15)

| Value | Fill color | Font color |
|-------|-----------|------------|
| `complete` | `C6EFCE` | `006100` |
| `timeout` / `CAPTCHA` / `login_wall` / `redirect` / `blocked` / `SPA` / `no_chrome` | `FFEB9C` | `9C6500` |
| `not_found` / `closed` | `FFC7CE` | `9C0006` |
| `Listing only` | `D9E2F3` | `2F5496` |

## Application Status (column 16)

| Value | Fill color | Font color |
|-------|-----------|------------|
| `new` | none (white) | default |
| `Not Applied` | `FFEB9C` | `9C6500` |
| `Applied` | `D9E2F3` | `2F5496` |
| `Interview` | `C6EFCE` | `006100` |
| `Rejected` | `FFC7CE` | `9C0006` |
| `Offer` | `E2EFDA` | `375623` (bold) |
| `not found` | `FFC7CE` | `9C0006` |
| `skipped` | `D9D9D9` | `595959` |

## Canada Eligible (column 17)

| Value | Fill color | Font color |
|-------|-----------|------------|
| `yes` | `C6EFCE` | `006100` |
| `no` | `FFC7CE` | `9C0006` |
| `unclear` | `FFEB9C` | `9C6500` |
| `Likely` | `D9E2F3` | `2F5496` |

## Quick Reference

```python
from openpyxl.styles import PatternFill, Font

GREEN_FILL = PatternFill(start_color="C6EFCE", fill_type="solid")
GREEN_FONT = Font(color="006100")
YELLOW_FILL = PatternFill(start_color="FFEB9C", fill_type="solid")
YELLOW_FONT = Font(color="9C6500")
RED_FILL = PatternFill(start_color="FFC7CE", fill_type="solid")
RED_FONT = Font(color="9C0006")
BLUE_FILL = PatternFill(start_color="D9E2F3", fill_type="solid")
BLUE_FONT = Font(color="2F5496")
OFFER_FILL = PatternFill(start_color="E2EFDA", fill_type="solid")
OFFER_FONT = Font(color="375623", bold=True)
LINK_FONT = Font(color="0563C1", underline="single")
```

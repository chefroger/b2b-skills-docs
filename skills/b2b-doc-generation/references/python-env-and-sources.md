# B2B Document Generation — Reference Notes

## Python Environment (Trade System)

The Trade server runs in a dedicated venv at `/Users/rogerlau/.trade/venv/bin/python`.
**Always use this path** — system Python (`python3`, `/usr/local/bin/python3`) lacks `docx`, `pptx`, `openpyxl`, `PIL`.

```bash
# WRONG — will fail with ModuleNotFoundError
python3 -c "from pptx import Presentation"
# ModuleNotFoundError: No module named 'pptx'

# CORRECT
/Users/rogerlau/.trade/venv/bin/python -c "from pptx import Presentation"
```

The venv is also used by the running Trade server process (`ps aux | grep trade`).

---

## Finding Product Data in the [Company Name] Document Library

When generating documents for 科辰, key source files:

| Source | Path | Content |
|--------|------|---------|
| **Insulator specs (PPTX)** | `~/Desktop/科辰/绝缘子_副本/绝缘子参数.pptx` | 8 FXBW/FZSW models with voltage/height/creepage/load specs |
| **Full product catalog (PPTX)** | `~/Desktop/科辰/科辰产品册_副本/[Company Name] Product Catalog-2025.pptx` | 40 slides: company profile, 10 categories of hardware |
| **Product categories (XLSX)** | `~/Desktop/科辰/电力相关产品清单_副本.xlsx` | 10 sheet categories (电力金具, 绝缘子, 中高压电气, etc.) |
| **Complete product report** | `~/Desktop/科辰/任务报告-产品数据列表.md` | Prior-generated summary of all 10 product categories with 200+ models |

---

## Color Schemes by Industry

| Industry | Primary | Accent | Hex |
|----------|---------|--------|-----|
| Industrial / Power / Manufacturing | Deep navy | Gold | `#0B2A4A` + `#D4A853` |
| Clean corporate / Technology | Teal | White | `#0E7490` + white |
| Agriculture / Natural | Forest green | Cream | `#2C5F2D` + `#F5F0E1` |

---

## PPTX Text Extraction

```python
# Extract text from any PPTX catalog
/Users/rogerlau/.trade/venv/bin/python -c "
from pptx import Presentation
prs = Presentation('/path/to/catalog.pptx')
for i, slide in enumerate(prs.slides):
    texts = []
    for shape in slide.shapes:
        if hasattr(shape, 'text') and shape.text.strip():
            texts.append(shape.text.strip())
    if texts:
        print(f'=== Slide {i+1} ===')
        for t in texts[:20]: print(t)
"
```

---

## XLSX Data Extraction

```python
# Read all sheets in an Excel product list
/Users/rogerlau/.trade/venv/bin/python -c "
import openpyxl
wb = openpyxl.load_workbook('/path/to/file.xlsx', data_only=True)
print('Sheets:', wb.sheetnames)
for name in wb.sheetnames:
    ws = wb[name]
    print(f'=== {name} ({ws.max_row} rows) ===')
    for row in ws.iter_rows(min_row=1, max_row=min(30, ws.max_row), values_only=True):
        if any(cell is not None for cell in row):
            print(row)
"
```

---

## DOCX Generator Script Pattern

For multi-section documents, write generator to a `.py` file first, then run with Trade venv Python.

```python
from docx import Document
from docx.shared import Pt, RGBColor, Cm
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.enum.table import WD_TABLE_ALIGNMENT
from docx.oxml.ns import qn
from docx.oxml import OxmlElement
import os

doc = Document()
for section in doc.sections:
    section.top_margin = Cm(2); section.bottom_margin = Cm(2)
    section.left_margin = Cm(2.5); section.right_margin = Cm(2.5)

def set_cell_bg(cell, hex_color):
    tc = cell._tc; tcPr = tc.get_or_add_tcPr()
    shd = OxmlElement('w:shd')
    shd.set(qn('w:fill'), hex_color); tcPr.append(shd)

NAVY = (0x0B, 0x2A, 0x4A); GOLD = (0xD4, 0xA8, 0x53); WHITE = (0xFF, 0xFF, 0xFF)

def add_table_header(tbl, headers, bg='0B2A4A'):
    for i, h in enumerate(headers):
        cell = tbl.rows[0].cells[i]
        cell.text = h
        set_cell_bg(cell, bg)
        p = cell.paragraphs[0]; p.alignment = WD_ALIGN_PARAGRAPH.CENTER
        run = p.runs[0]; run.font.bold = True
        run.font.color.rgb = RGBColor(*WHITE); run.font.size = Pt(9)

out_path = '/path/to/output.docx'
os.makedirs(os.path.dirname(out_path), exist_ok=True)
doc.save(out_path)
print(f'Saved: {out_path}, Size: {os.path.getsize(out_path):,} bytes')
```

Save scripts to `~/.trade/companies/{slug}/output/gen_{docname}.py`.

---

## Verification Commands

```python
# Verify DOCX
from docx import Document
doc = Document('/path/to/output.docx')
print('Paragraphs:', len(doc.paragraphs), 'Tables:', len(doc.tables))
for i, tbl in enumerate(doc.tables):
    print(f'  Table {i+1}: {len(tbl.rows)} rows x {len(tbl.columns)} cols')
for p in doc.paragraphs[:6]:
    if p.text.strip(): print(repr(p.text[:80]))

# Verify PPTX
from pptx import Presentation
prs = Presentation('/path/to/output.pptx')
print(f'Total slides: {len(prs.slides)}')
for i, slide in enumerate(prs.slides, 1):
    title = slide.shapes.title.text if slide.shapes.title else '(no title)'
    print(f'Slide {i}: {title}')
```

---

## Session Notes (2026-05-29)

### Insulator product data extracted this session
- Source: `~/Desktop/科辰/绝缘子_副本/绝缘子参数.pptx` (8 models: FZSW-69KV&70, FZSW-138KV&70, FXBW-138KV-120, FXBW-138KV-160, FXBW-69-100, FXBW-138-100, 2×FXBW-69-120)
- Source: `~/Desktop/科辰/科辰产品册_副本/[Company Name] Product Catalog-2025.pptx` (40 slides, 10 categories)
- Source: `~/Desktop/科辰/电力相关产品清单_副本.xlsx` (10 sheet categories)
- Generated: `[Company Name]_Product_Specification_Sheet.docx` (40.9 KB, 7 tables, all English)

### Key [Company Name] contacts (from catalog)
- Nancy Wu ([contact.email])
- WeChat: +86 15502257380
- WhatsApp: +86 17802233882
- Website: www.kechenelectrical.com
- Factory: Dingcheng Electric Power Equipment Manufacturing Co., Ltd. (Renqiu, Hebei)
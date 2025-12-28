# New Account Due Diligence Generator

This folder contains a web-based DOCX generator and a Python CLI for the
"New Account Due Diligence" report. The web page fills 3 fields and appends
site-visit photos at the end of the Word document.

## Files
- `新开户尽职调查表模版.docx`: The Word template.
- `新开户尽职调查表网页版.html`: The web UI (GitHub Pages or local file).
- `新开户尽职调查表网页版.py`: The Python generator (CLI + interactive).

## Web usage
1. Open `新开户尽职调查表网页版.html` (local or GitHub Pages).
2. Upload the template DOCX.
3. Fill required fields.
4. Add photos (optional).
5. Click "生成 DOCX".

The web generator requires these placeholders in the template:
```
{{客户名称}}
{{行业分类}}
{{经营地址}}
```

Photos are inserted after the paragraph containing "上门核实图片".
If the paragraph is missing, photos are appended to the end of the document.

## Python usage
Interactive mode:
```
python3 新开户尽职调查表网页版.py --interactive
```

One-shot mode:
```
python3 新开户尽职调查表网页版.py \
  --customer "ACME Co., Ltd." \
  --industry "L7241" \
  --address "Xiamen City..." \
  --photos "/path/to/photos"
```

## Notes / Troubleshooting
- The web page loads PizZip from a CDN. A network connection is required the
  first time unless you bundle the library locally.
- If photos are missing in DOCX, try JPG/PNG (some phones capture HEIC).
- On iPhone, allow photo access and keep the page open until generation ends.

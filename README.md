# pagespool integrations

Seven open-source document engines behind one API key: Docling, MarkItDown, WeasyPrint, veraPDF, Gotenberg, OCRmyPDF, EPUBCheck.

pagespool hosts seven open-source document engines under their own names: Docling, MarkItDown, WeasyPrint, veraPDF, Gotenberg, OCRmyPDF and EPUBCheck. Each engine has its own REST API, MCP server and free tool, and one API key and one credit balance pay for all seven. Docling, veraPDF and Gotenberg answer on their own routes, so their clients work with a new base URL. The servers are in Germany. The free plan has 100 credits a month and needs no card.

Official integrations for the [pagespool API](https://pagespool.com), generated from its [OpenAPI document](openapi.json) and published from this repository.

## Get an API key

[Create a key](https://pagespool.com/go/connectors?to=/app/api-keys) and send it in the `X-API-Key` header.

## Integrations

- **Python SDK** — `pip install pagespool` · [PyPI](https://pypi.org/project/pagespool/)

## Operations

| Operation | Endpoint | What it does |
|---|---|---|
| `get_me` | `GET /v1/me` | Your plan, remaining requests, and remaining credits |
| `get_job` | `GET /v1/jobs/{job_id}` | Get one queued job by ID |
| `list_jobs` | `GET /v1/jobs` | List your queued jobs, newest first |
| `epubcheck_check` | `POST /v1/epubcheck/check` | Check an EPUB file with EPUBCheck |
| `ocrmypdf_submit` | `POST /v1/ocrmypdf/jobs` | OCR a scanned PDF or image, 2 credits per page |
| `ocrmypdf_get_result` | `GET /v1/ocrmypdf/jobs/{job_id}/result` | Download the searchable PDF of an OCR job |
| `gotenberg_chromium_convert_html` | `POST /v1/gotenberg/forms/chromium/convert/html` | Convert an HTML file to PDF with Chromium |
| `gotenberg_chromium_convert_url` | `POST /v1/gotenberg/forms/chromium/convert/url` | Convert a web page to PDF with Chromium |
| `gotenberg_chromium_convert_markdown` | `POST /v1/gotenberg/forms/chromium/convert/markdown` | Convert Markdown files to PDF with Chromium |
| `gotenberg_chromium_screenshot_html` | `POST /v1/gotenberg/forms/chromium/screenshot/html` | Screenshot an HTML file with Chromium |
| `gotenberg_chromium_screenshot_url` | `POST /v1/gotenberg/forms/chromium/screenshot/url` | Screenshot a web page with Chromium |
| `gotenberg_chromium_screenshot_markdown` | `POST /v1/gotenberg/forms/chromium/screenshot/markdown` | Screenshot Markdown files with Chromium |
| `gotenberg_libreoffice_convert` | `POST /v1/gotenberg/forms/libreoffice/convert` | Convert office documents to PDF with LibreOffice |
| `gotenberg_pdf_pipe` | `POST /v1/gotenberg/forms/pdf/pipe` | Run a list of stages on PDFs |
| `gotenberg_pdf_info` | `POST /v1/gotenberg/forms/pdf/info` | Read the page count and properties of PDFs |
| `gotenberg_pdf_merge` | `POST /v1/gotenberg/forms/pdf/merge` | Merge PDFs |
| `gotenberg_pdf_split` | `POST /v1/gotenberg/forms/pdf/split` | Split PDFs |
| `gotenberg_pdf_select` | `POST /v1/gotenberg/forms/pdf/select` | Keep selected pages of PDFs |
| `gotenberg_pdf_delete` | `POST /v1/gotenberg/forms/pdf/delete` | Delete pages of PDFs |
| `gotenberg_pdf_insert` | `POST /v1/gotenberg/forms/pdf/insert` | Insert pages into PDFs |
| `gotenberg_pdf_rotate` | `POST /v1/gotenberg/forms/pdf/rotate` | Rotate the pages of PDFs |
| `gotenberg_pdf_compose` | `POST /v1/gotenberg/forms/pdf/compose` | Compose pages of PDFs on new pages |
| `gotenberg_pdf_render` | `POST /v1/gotenberg/forms/pdf/render` | Render the pages of PDFs as images |
| `gotenberg_pdf_stamp_text` | `POST /v1/gotenberg/forms/pdf/stamp-text` | Stamp text on PDFs |
| `gotenberg_pdf_stamp_image` | `POST /v1/gotenberg/forms/pdf/stamp-image` | Stamp an image on PDFs |
| `gotenberg_pdf_stamp_pdf` | `POST /v1/gotenberg/forms/pdf/stamp-pdf` | Stamp a PDF page on PDFs |
| `gotenberg_pdf_metadata` | `POST /v1/gotenberg/forms/pdf/metadata` | Read the metadata of PDFs |
| `gotenberg_pdf_set_metadata` | `POST /v1/gotenberg/forms/pdf/set-metadata` | Write the metadata of PDFs |
| `gotenberg_pdf_bookmarks` | `POST /v1/gotenberg/forms/pdf/bookmarks` | Read the bookmarks of PDFs |
| `gotenberg_pdf_set_bookmarks` | `POST /v1/gotenberg/forms/pdf/set-bookmarks` | Write the bookmarks of PDFs |
| `gotenberg_pdf_attach` | `POST /v1/gotenberg/forms/pdf/attach` | Attach files to PDFs |
| `gotenberg_pdf_attachments` | `POST /v1/gotenberg/forms/pdf/attachments` | List the attachments of PDFs |
| `gotenberg_pdf_detach` | `POST /v1/gotenberg/forms/pdf/detach` | Remove an attachment from PDFs |
| `gotenberg_pdf_extract_attachments` | `POST /v1/gotenberg/forms/pdf/extract-attachments` | Extract the attachments of PDFs |
| `gotenberg_pdf_form` | `POST /v1/gotenberg/forms/pdf/form` | List the form fields of PDFs |
| `gotenberg_pdf_set_form` | `POST /v1/gotenberg/forms/pdf/set-form` | Fill the form fields of PDFs |
| `gotenberg_pdf_flatten_form` | `POST /v1/gotenberg/forms/pdf/flatten-form` | Flatten the form fields of PDFs |
| `gotenberg_pdf_extract_text` | `POST /v1/gotenberg/forms/pdf/extract-text` | Extract the text of PDFs |
| `gotenberg_pdf_redact` | `POST /v1/gotenberg/forms/pdf/redact` | Redact content from PDFs |
| `gotenberg_pdf_optimize` | `POST /v1/gotenberg/forms/pdf/optimize` | Optimize PDFs |
| `gotenberg_pdf_convert_colors` | `POST /v1/gotenberg/forms/pdf/convert-colors` | Convert the colors of PDFs |
| `gotenberg_pdf_flatten_transparency` | `POST /v1/gotenberg/forms/pdf/flatten-transparency` | Flatten the transparency of PDFs |
| `gotenberg_pdf_remediate` | `POST /v1/gotenberg/forms/pdf/remediate` | Make PDFs conform to PDF/A or PDF/UA |
| `gotenberg_pdf_validate` | `POST /v1/gotenberg/forms/pdf/validate` | Validate PDFs against PDF/A or PDF/UA |
| `gotenberg_pdf_autotag` | `POST /v1/gotenberg/forms/pdf/autotag` | Add structure tags to PDFs |
| `gotenberg_pdf_encrypt` | `POST /v1/gotenberg/forms/pdf/encrypt` | Encrypt PDFs |
| `gotenberg_pdf_decrypt` | `POST /v1/gotenberg/forms/pdf/decrypt` | Decrypt PDFs |
| `gotenberg_pdf_sign` | `POST /v1/gotenberg/forms/pdf/sign` | Sign PDFs with a certificate |
| `gotenberg_pdf_timestamp` | `POST /v1/gotenberg/forms/pdf/timestamp` | Timestamp PDFs |
| `gotenberg_health` | `GET /v1/gotenberg/health` | Check that Gotenberg is up |
| `gotenberg_version` | `GET /v1/gotenberg/version` | Show Gotenberg's version |
| `verapdf_validate_auto` | `POST /v1/verapdf/api/validate/auto` | Check a PDF against the PDF/A part it declares |
| `verapdf_validate_1a` | `POST /v1/verapdf/api/validate/1a` | Check a PDF against PDF/A-1a |
| `verapdf_validate_1b` | `POST /v1/verapdf/api/validate/1b` | Check a PDF against PDF/A-1b |
| `verapdf_validate_2a` | `POST /v1/verapdf/api/validate/2a` | Check a PDF against PDF/A-2a |
| `verapdf_validate_2b` | `POST /v1/verapdf/api/validate/2b` | Check a PDF against PDF/A-2b |
| `verapdf_validate_2u` | `POST /v1/verapdf/api/validate/2u` | Check a PDF against PDF/A-2u |
| `verapdf_validate_3a` | `POST /v1/verapdf/api/validate/3a` | Check a PDF against PDF/A-3a |
| `verapdf_validate_3b` | `POST /v1/verapdf/api/validate/3b` | Check a PDF against PDF/A-3b |
| `verapdf_validate_3u` | `POST /v1/verapdf/api/validate/3u` | Check a PDF against PDF/A-3u |
| `verapdf_validate_4` | `POST /v1/verapdf/api/validate/4` | Check a PDF against PDF/A-4 |
| `verapdf_validate_4e` | `POST /v1/verapdf/api/validate/4e` | Check a PDF against PDF/A-4e |
| `verapdf_validate_4f` | `POST /v1/verapdf/api/validate/4f` | Check a PDF against PDF/A-4f |
| `verapdf_validate_ua1` | `POST /v1/verapdf/api/validate/ua1` | Check a PDF against PDF/UA-1 |
| `verapdf_validate_ua2` | `POST /v1/verapdf/api/validate/ua2` | Check a PDF against PDF/UA-2 |
| `verapdf_validate_wt1a` | `POST /v1/verapdf/api/validate/wt1a` | Check a PDF against WTPDF 1.0 Accessibility |
| `verapdf_validate_wt1r` | `POST /v1/verapdf/api/validate/wt1r` | Check a PDF against WTPDF 1.0 Reuse |
| `verapdf_info` | `GET /v1/verapdf/api/info` | Get the veraPDF server's environment |
| `verapdf_list_profiles` | `GET /v1/verapdf/api/profiles` | List veraPDF's validation profiles |
| `verapdf_get_profile` | `GET /v1/verapdf/api/profiles/{profile_id}` | Get one veraPDF validation profile |
| `weasyprint_render` | `POST /v1/weasyprint/render` | Render an HTML document to a PDF |
| `markitdown_convert` | `POST /v1/markitdown/convert` | Convert a document to Markdown with MarkItDown |
| `docling_convert_file` | `POST /v1/docling/v1/convert/file` | Convert an uploaded document, waiting up to 50 s (1 credit per PDF page, 10 per other file) |
| `docling_convert_file_async` | `POST /v1/docling/v1/convert/file/async` | Queue an uploaded document for conversion (1 credit per PDF page, 10 per other file) |
| `docling_convert_source` | `POST /v1/docling/v1/convert/source` | Convert a document from a URL or base64, waiting up to 50 s (1 credit per PDF page, 10 per other file) |
| `docling_convert_source_async` | `POST /v1/docling/v1/convert/source/async` | Queue a document from a URL or base64 for conversion (1 credit per PDF page, 10 per other file) |
| `docling_status_poll` | `GET /v1/docling/v1/status/poll/{task_id}` | Check a conversion |
| `docling_result` | `GET /v1/docling/v1/result/{task_id}` | Download a conversion's result |

API reference: https://pagespool.com/docs · Base URL: `https://api.pagespool.com`

## Support

https://pagespool.com/support

Every file listed in `.generated` is rebuilt from the live API; changes to them are overwritten.

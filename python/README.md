# Pagespool — Python SDK

Seven open-source document engines behind one API key: Docling, MarkItDown, WeasyPrint, veraPDF, Gotenberg, OCRmyPDF, EPUBCheck.

```sh
pip install pagespool
```

[Get an API key](https://pagespool.com/go/pypi-sdk?to=/app/api-keys) and pass it to the client:

```python
import os

from pagespool import AuthenticatedClient
from pagespool.api.account import get_me

client = AuthenticatedClient(
    base_url="https://api.pagespool.com",
    token=os.environ["PAGESPOOL_API_KEY"],
    auth_header_name="X-API-Key",
    prefix="",
)
print(get_me.sync(client=client))
```

Every operation is a module with `sync`, `sync_detailed`, `asyncio` and `asyncio_detailed`; file fields take a `pagespool.types.File(payload=..., file_name=..., mime_type=...)`.

`ocrmypdf_submit` queues a job: poll `get_job` until its `status` is `succeeded` or `failed`, then fetch `ocrmypdf_get_result`.

`docling_convert_file_async` queues a job: poll `docling_status_poll` until its `status` is `succeeded` or `failed`, then fetch `docling_result`.

`docling_convert_source_async` queues a job: poll `docling_status_poll` until its `status` is `succeeded` or `failed`, then fetch `docling_result`.

## Operations

| Operation | Module | What it does |
|---|---|---|
| `GET /v1/me` | `pagespool.api.account.get_me` | Your plan, remaining requests, and remaining credits |
| `GET /v1/jobs/{job_id}` | `pagespool.api.jobs.get_job` | Get one queued job by ID |
| `GET /v1/jobs` | `pagespool.api.jobs.list_jobs` | List your queued jobs, newest first |
| `POST /v1/epubcheck/check` | `pagespool.api.epubcheck.epubcheck_check` | Check an EPUB file with EPUBCheck |
| `POST /v1/ocrmypdf/jobs` | `pagespool.api.ocrmypdf.ocrmypdf_submit` | OCR a scanned PDF or image, 2 credits per page |
| `GET /v1/ocrmypdf/jobs/{job_id}/result` | `pagespool.api.ocrmypdf.ocrmypdf_get_result` | Download the searchable PDF of an OCR job |
| `POST /v1/gotenberg/forms/chromium/convert/html` | `pagespool.api.gotenberg.gotenberg_chromium_convert_html` | Convert an HTML file to PDF with Chromium |
| `POST /v1/gotenberg/forms/chromium/convert/url` | `pagespool.api.gotenberg.gotenberg_chromium_convert_url` | Convert a web page to PDF with Chromium |
| `POST /v1/gotenberg/forms/chromium/convert/markdown` | `pagespool.api.gotenberg.gotenberg_chromium_convert_markdown` | Convert Markdown files to PDF with Chromium |
| `POST /v1/gotenberg/forms/chromium/screenshot/html` | `pagespool.api.gotenberg.gotenberg_chromium_screenshot_html` | Screenshot an HTML file with Chromium |
| `POST /v1/gotenberg/forms/chromium/screenshot/url` | `pagespool.api.gotenberg.gotenberg_chromium_screenshot_url` | Screenshot a web page with Chromium |
| `POST /v1/gotenberg/forms/chromium/screenshot/markdown` | `pagespool.api.gotenberg.gotenberg_chromium_screenshot_markdown` | Screenshot Markdown files with Chromium |
| `POST /v1/gotenberg/forms/libreoffice/convert` | `pagespool.api.gotenberg.gotenberg_libreoffice_convert` | Convert office documents to PDF with LibreOffice |
| `POST /v1/gotenberg/forms/pdf/pipe` | `pagespool.api.gotenberg.gotenberg_pdf_pipe` | Run a list of stages on PDFs |
| `POST /v1/gotenberg/forms/pdf/info` | `pagespool.api.gotenberg.gotenberg_pdf_info` | Read the page count and properties of PDFs |
| `POST /v1/gotenberg/forms/pdf/merge` | `pagespool.api.gotenberg.gotenberg_pdf_merge` | Merge PDFs |
| `POST /v1/gotenberg/forms/pdf/split` | `pagespool.api.gotenberg.gotenberg_pdf_split` | Split PDFs |
| `POST /v1/gotenberg/forms/pdf/select` | `pagespool.api.gotenberg.gotenberg_pdf_select` | Keep selected pages of PDFs |
| `POST /v1/gotenberg/forms/pdf/delete` | `pagespool.api.gotenberg.gotenberg_pdf_delete` | Delete pages of PDFs |
| `POST /v1/gotenberg/forms/pdf/insert` | `pagespool.api.gotenberg.gotenberg_pdf_insert` | Insert pages into PDFs |
| `POST /v1/gotenberg/forms/pdf/rotate` | `pagespool.api.gotenberg.gotenberg_pdf_rotate` | Rotate the pages of PDFs |
| `POST /v1/gotenberg/forms/pdf/compose` | `pagespool.api.gotenberg.gotenberg_pdf_compose` | Compose pages of PDFs on new pages |
| `POST /v1/gotenberg/forms/pdf/render` | `pagespool.api.gotenberg.gotenberg_pdf_render` | Render the pages of PDFs as images |
| `POST /v1/gotenberg/forms/pdf/stamp-text` | `pagespool.api.gotenberg.gotenberg_pdf_stamp_text` | Stamp text on PDFs |
| `POST /v1/gotenberg/forms/pdf/stamp-image` | `pagespool.api.gotenberg.gotenberg_pdf_stamp_image` | Stamp an image on PDFs |
| `POST /v1/gotenberg/forms/pdf/stamp-pdf` | `pagespool.api.gotenberg.gotenberg_pdf_stamp_pdf` | Stamp a PDF page on PDFs |
| `POST /v1/gotenberg/forms/pdf/metadata` | `pagespool.api.gotenberg.gotenberg_pdf_metadata` | Read the metadata of PDFs |
| `POST /v1/gotenberg/forms/pdf/set-metadata` | `pagespool.api.gotenberg.gotenberg_pdf_set_metadata` | Write the metadata of PDFs |
| `POST /v1/gotenberg/forms/pdf/bookmarks` | `pagespool.api.gotenberg.gotenberg_pdf_bookmarks` | Read the bookmarks of PDFs |
| `POST /v1/gotenberg/forms/pdf/set-bookmarks` | `pagespool.api.gotenberg.gotenberg_pdf_set_bookmarks` | Write the bookmarks of PDFs |
| `POST /v1/gotenberg/forms/pdf/attach` | `pagespool.api.gotenberg.gotenberg_pdf_attach` | Attach files to PDFs |
| `POST /v1/gotenberg/forms/pdf/attachments` | `pagespool.api.gotenberg.gotenberg_pdf_attachments` | List the attachments of PDFs |
| `POST /v1/gotenberg/forms/pdf/detach` | `pagespool.api.gotenberg.gotenberg_pdf_detach` | Remove an attachment from PDFs |
| `POST /v1/gotenberg/forms/pdf/extract-attachments` | `pagespool.api.gotenberg.gotenberg_pdf_extract_attachments` | Extract the attachments of PDFs |
| `POST /v1/gotenberg/forms/pdf/form` | `pagespool.api.gotenberg.gotenberg_pdf_form` | List the form fields of PDFs |
| `POST /v1/gotenberg/forms/pdf/set-form` | `pagespool.api.gotenberg.gotenberg_pdf_set_form` | Fill the form fields of PDFs |
| `POST /v1/gotenberg/forms/pdf/flatten-form` | `pagespool.api.gotenberg.gotenberg_pdf_flatten_form` | Flatten the form fields of PDFs |
| `POST /v1/gotenberg/forms/pdf/extract-text` | `pagespool.api.gotenberg.gotenberg_pdf_extract_text` | Extract the text of PDFs |
| `POST /v1/gotenberg/forms/pdf/redact` | `pagespool.api.gotenberg.gotenberg_pdf_redact` | Redact content from PDFs |
| `POST /v1/gotenberg/forms/pdf/optimize` | `pagespool.api.gotenberg.gotenberg_pdf_optimize` | Optimize PDFs |
| `POST /v1/gotenberg/forms/pdf/convert-colors` | `pagespool.api.gotenberg.gotenberg_pdf_convert_colors` | Convert the colors of PDFs |
| `POST /v1/gotenberg/forms/pdf/flatten-transparency` | `pagespool.api.gotenberg.gotenberg_pdf_flatten_transparency` | Flatten the transparency of PDFs |
| `POST /v1/gotenberg/forms/pdf/remediate` | `pagespool.api.gotenberg.gotenberg_pdf_remediate` | Make PDFs conform to PDF/A or PDF/UA |
| `POST /v1/gotenberg/forms/pdf/validate` | `pagespool.api.gotenberg.gotenberg_pdf_validate` | Validate PDFs against PDF/A or PDF/UA |
| `POST /v1/gotenberg/forms/pdf/autotag` | `pagespool.api.gotenberg.gotenberg_pdf_autotag` | Add structure tags to PDFs |
| `POST /v1/gotenberg/forms/pdf/encrypt` | `pagespool.api.gotenberg.gotenberg_pdf_encrypt` | Encrypt PDFs |
| `POST /v1/gotenberg/forms/pdf/decrypt` | `pagespool.api.gotenberg.gotenberg_pdf_decrypt` | Decrypt PDFs |
| `POST /v1/gotenberg/forms/pdf/sign` | `pagespool.api.gotenberg.gotenberg_pdf_sign` | Sign PDFs with a certificate |
| `POST /v1/gotenberg/forms/pdf/timestamp` | `pagespool.api.gotenberg.gotenberg_pdf_timestamp` | Timestamp PDFs |
| `GET /v1/gotenberg/health` | `pagespool.api.gotenberg.gotenberg_health` | Check that Gotenberg is up |
| `GET /v1/gotenberg/version` | `pagespool.api.gotenberg.gotenberg_version` | Show Gotenberg's version |
| `POST /v1/verapdf/api/validate/auto` | `pagespool.api.verapdf.verapdf_validate_auto` | Check a PDF against the PDF/A part it declares |
| `POST /v1/verapdf/api/validate/1a` | `pagespool.api.verapdf.verapdf_validate_1a` | Check a PDF against PDF/A-1a |
| `POST /v1/verapdf/api/validate/1b` | `pagespool.api.verapdf.verapdf_validate_1b` | Check a PDF against PDF/A-1b |
| `POST /v1/verapdf/api/validate/2a` | `pagespool.api.verapdf.verapdf_validate_2a` | Check a PDF against PDF/A-2a |
| `POST /v1/verapdf/api/validate/2b` | `pagespool.api.verapdf.verapdf_validate_2b` | Check a PDF against PDF/A-2b |
| `POST /v1/verapdf/api/validate/2u` | `pagespool.api.verapdf.verapdf_validate_2u` | Check a PDF against PDF/A-2u |
| `POST /v1/verapdf/api/validate/3a` | `pagespool.api.verapdf.verapdf_validate_3a` | Check a PDF against PDF/A-3a |
| `POST /v1/verapdf/api/validate/3b` | `pagespool.api.verapdf.verapdf_validate_3b` | Check a PDF against PDF/A-3b |
| `POST /v1/verapdf/api/validate/3u` | `pagespool.api.verapdf.verapdf_validate_3u` | Check a PDF against PDF/A-3u |
| `POST /v1/verapdf/api/validate/4` | `pagespool.api.verapdf.verapdf_validate_4` | Check a PDF against PDF/A-4 |
| `POST /v1/verapdf/api/validate/4e` | `pagespool.api.verapdf.verapdf_validate_4e` | Check a PDF against PDF/A-4e |
| `POST /v1/verapdf/api/validate/4f` | `pagespool.api.verapdf.verapdf_validate_4f` | Check a PDF against PDF/A-4f |
| `POST /v1/verapdf/api/validate/ua1` | `pagespool.api.verapdf.verapdf_validate_ua1` | Check a PDF against PDF/UA-1 |
| `POST /v1/verapdf/api/validate/ua2` | `pagespool.api.verapdf.verapdf_validate_ua2` | Check a PDF against PDF/UA-2 |
| `POST /v1/verapdf/api/validate/wt1a` | `pagespool.api.verapdf.verapdf_validate_wt1a` | Check a PDF against WTPDF 1.0 Accessibility |
| `POST /v1/verapdf/api/validate/wt1r` | `pagespool.api.verapdf.verapdf_validate_wt1r` | Check a PDF against WTPDF 1.0 Reuse |
| `GET /v1/verapdf/api/info` | `pagespool.api.verapdf.verapdf_info` | Get the veraPDF server's environment |
| `GET /v1/verapdf/api/profiles` | `pagespool.api.verapdf.verapdf_list_profiles` | List veraPDF's validation profiles |
| `GET /v1/verapdf/api/profiles/{profile_id}` | `pagespool.api.verapdf.verapdf_get_profile` | Get one veraPDF validation profile |
| `POST /v1/weasyprint/render` | `pagespool.api.weasyprint.weasyprint_render` | Render an HTML document to a PDF |
| `POST /v1/markitdown/convert` | `pagespool.api.markitdown.markitdown_convert` | Convert a document to Markdown with MarkItDown |
| `POST /v1/docling/v1/convert/file` | `pagespool.api.docling.docling_convert_file` | Convert an uploaded document, waiting up to 50 s (1 credit per PDF page, 10 per other file) |
| `POST /v1/docling/v1/convert/file/async` | `pagespool.api.docling.docling_convert_file_async` | Queue an uploaded document for conversion (1 credit per PDF page, 10 per other file) |
| `POST /v1/docling/v1/convert/source` | `pagespool.api.docling.docling_convert_source` | Convert a document from a URL or base64, waiting up to 50 s (1 credit per PDF page, 10 per other file) |
| `POST /v1/docling/v1/convert/source/async` | `pagespool.api.docling.docling_convert_source_async` | Queue a document from a URL or base64 for conversion (1 credit per PDF page, 10 per other file) |
| `GET /v1/docling/v1/status/poll/{task_id}` | `pagespool.api.docling.docling_status_poll` | Check a conversion |
| `GET /v1/docling/v1/result/{task_id}` | `pagespool.api.docling.docling_result` | Download a conversion's result |

Generated with openapi-python-client from [`openapi.sdk.json`](../openapi.sdk.json). API reference: https://pagespool.com/docs · Support: https://pagespool.com/support

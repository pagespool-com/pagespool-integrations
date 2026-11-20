# pagespool

Seven open-source document engines behind one API key: Docling, MarkItDown, WeasyPrint, veraPDF, Gotenberg, OCRmyPDF, EPUBCheck.

pagespool hosts seven open-source document engines under their own names: Docling, MarkItDown, WeasyPrint, veraPDF, Gotenberg, OCRmyPDF and EPUBCheck. Each engine has its own REST API, MCP server and free tool, and one API key and one credit balance pay for all seven. Docling, veraPDF and Gotenberg answer on their own routes, so their clients work with a new base URL. The servers are in Germany. The free plan has 100 credits a month and needs no card.

A Dify tool plugin for the [pagespool API](https://pagespool.com).

## Setup

1. Install **pagespool** from the Dify Marketplace (Plugins → Marketplace).
2. Open the plugin's tool settings and choose **Authorize**. Leave the API key empty to try the tools on the free daily allowance, or paste a [free pagespool API key](https://pagespool.com/go/dify?to=/app/api-keys) for your account's monthly credits.

Without a key, every call from one network address shares the free daily allowance. On Dify Cloud the calls come from Dify's servers, so other users may draw on the same allowance. Once it is used up, the tool's error says where to get a key.

## Usage

Add the tools to a workflow, chatflow or agent. File inputs take a Dify file; JSON object and array inputs take JSON text. JSON answers come back as JSON, text and XML as text, documents as files. A tool that queues a job returns its id: poll it with the job tool, then fetch its result with the matching result tool. A tool with a Form fields input sends the JSON object given there as further form fields of its request.

| Tool | Endpoint | What it does |
|---|---|---|
| Get me | `GET /v1/me` | Your plan, remaining requests, and remaining credits |
| Get job | `GET /v1/jobs/{job_id}` | Get one queued job by ID |
| List jobs | `GET /v1/jobs` | List your queued jobs, newest first |
| Epubcheck check | `POST /v1/epubcheck/check` | Check an EPUB file with EPUBCheck |
| Ocrmypdf submit | `POST /v1/ocrmypdf/jobs` | OCR a scanned PDF or image, 2 credits per page |
| Ocrmypdf get result | `GET /v1/ocrmypdf/jobs/{job_id}/result` | Download the searchable PDF of an OCR job |
| Gotenberg chromium convert HTML | `POST /v1/gotenberg/forms/chromium/convert/html` | Convert an HTML file to PDF with Chromium |
| Gotenberg chromium convert URL | `POST /v1/gotenberg/forms/chromium/convert/url` | Convert a web page to PDF with Chromium |
| Gotenberg chromium convert markdown | `POST /v1/gotenberg/forms/chromium/convert/markdown` | Convert Markdown files to PDF with Chromium |
| Gotenberg chromium screenshot HTML | `POST /v1/gotenberg/forms/chromium/screenshot/html` | Screenshot an HTML file with Chromium |
| Gotenberg chromium screenshot URL | `POST /v1/gotenberg/forms/chromium/screenshot/url` | Screenshot a web page with Chromium |
| Gotenberg chromium screenshot markdown | `POST /v1/gotenberg/forms/chromium/screenshot/markdown` | Screenshot Markdown files with Chromium |
| Gotenberg libreoffice convert | `POST /v1/gotenberg/forms/libreoffice/convert` | Convert office documents to PDF with LibreOffice |
| Gotenberg PDF pipe | `POST /v1/gotenberg/forms/pdf/pipe` | Run a list of stages on PDFs |
| Gotenberg PDF info | `POST /v1/gotenberg/forms/pdf/info` | Read the page count and properties of PDFs |
| Gotenberg PDF merge | `POST /v1/gotenberg/forms/pdf/merge` | Merge PDFs |
| Gotenberg PDF split | `POST /v1/gotenberg/forms/pdf/split` | Split PDFs |
| Gotenberg PDF select | `POST /v1/gotenberg/forms/pdf/select` | Keep selected pages of PDFs |
| Gotenberg PDF delete | `POST /v1/gotenberg/forms/pdf/delete` | Delete pages of PDFs |
| Gotenberg PDF insert | `POST /v1/gotenberg/forms/pdf/insert` | Insert pages into PDFs |
| Gotenberg PDF rotate | `POST /v1/gotenberg/forms/pdf/rotate` | Rotate the pages of PDFs |
| Gotenberg PDF compose | `POST /v1/gotenberg/forms/pdf/compose` | Compose pages of PDFs on new pages |
| Gotenberg PDF render | `POST /v1/gotenberg/forms/pdf/render` | Render the pages of PDFs as images |
| Gotenberg PDF stamp text | `POST /v1/gotenberg/forms/pdf/stamp-text` | Stamp text on PDFs |
| Gotenberg PDF stamp image | `POST /v1/gotenberg/forms/pdf/stamp-image` | Stamp an image on PDFs |
| Gotenberg PDF stamp PDF | `POST /v1/gotenberg/forms/pdf/stamp-pdf` | Stamp a PDF page on PDFs |
| Gotenberg PDF metadata | `POST /v1/gotenberg/forms/pdf/metadata` | Read the metadata of PDFs |
| Gotenberg PDF set metadata | `POST /v1/gotenberg/forms/pdf/set-metadata` | Write the metadata of PDFs |
| Gotenberg PDF bookmarks | `POST /v1/gotenberg/forms/pdf/bookmarks` | Read the bookmarks of PDFs |
| Gotenberg PDF set bookmarks | `POST /v1/gotenberg/forms/pdf/set-bookmarks` | Write the bookmarks of PDFs |
| Gotenberg PDF attach | `POST /v1/gotenberg/forms/pdf/attach` | Attach files to PDFs |
| Gotenberg PDF attachments | `POST /v1/gotenberg/forms/pdf/attachments` | List the attachments of PDFs |
| Gotenberg PDF detach | `POST /v1/gotenberg/forms/pdf/detach` | Remove an attachment from PDFs |
| Gotenberg PDF extract attachments | `POST /v1/gotenberg/forms/pdf/extract-attachments` | Extract the attachments of PDFs |
| Gotenberg PDF form | `POST /v1/gotenberg/forms/pdf/form` | List the form fields of PDFs |
| Gotenberg PDF set form | `POST /v1/gotenberg/forms/pdf/set-form` | Fill the form fields of PDFs |
| Gotenberg PDF flatten form | `POST /v1/gotenberg/forms/pdf/flatten-form` | Flatten the form fields of PDFs |
| Gotenberg PDF extract text | `POST /v1/gotenberg/forms/pdf/extract-text` | Extract the text of PDFs |
| Gotenberg PDF redact | `POST /v1/gotenberg/forms/pdf/redact` | Redact content from PDFs |
| Gotenberg PDF optimize | `POST /v1/gotenberg/forms/pdf/optimize` | Optimize PDFs |
| Gotenberg PDF convert colors | `POST /v1/gotenberg/forms/pdf/convert-colors` | Convert the colors of PDFs |
| Gotenberg PDF flatten transparency | `POST /v1/gotenberg/forms/pdf/flatten-transparency` | Flatten the transparency of PDFs |
| Gotenberg PDF remediate | `POST /v1/gotenberg/forms/pdf/remediate` | Make PDFs conform to PDF/A or PDF/UA |
| Gotenberg PDF validate | `POST /v1/gotenberg/forms/pdf/validate` | Validate PDFs against PDF/A or PDF/UA |
| Gotenberg PDF autotag | `POST /v1/gotenberg/forms/pdf/autotag` | Add structure tags to PDFs |
| Gotenberg PDF encrypt | `POST /v1/gotenberg/forms/pdf/encrypt` | Encrypt PDFs |
| Gotenberg PDF decrypt | `POST /v1/gotenberg/forms/pdf/decrypt` | Decrypt PDFs |
| Gotenberg PDF sign | `POST /v1/gotenberg/forms/pdf/sign` | Sign PDFs with a certificate |
| Gotenberg PDF timestamp | `POST /v1/gotenberg/forms/pdf/timestamp` | Timestamp PDFs |
| Gotenberg health | `GET /v1/gotenberg/health` | Check that Gotenberg is up |
| Gotenberg version | `GET /v1/gotenberg/version` | Show Gotenberg's version |
| Verapdf validate auto | `POST /v1/verapdf/api/validate/auto` | Check a PDF against the PDF/A part it declares |
| Verapdf validate 1a | `POST /v1/verapdf/api/validate/1a` | Check a PDF against PDF/A-1a |
| Verapdf validate 1b | `POST /v1/verapdf/api/validate/1b` | Check a PDF against PDF/A-1b |
| Verapdf validate 2a | `POST /v1/verapdf/api/validate/2a` | Check a PDF against PDF/A-2a |
| Verapdf validate 2b | `POST /v1/verapdf/api/validate/2b` | Check a PDF against PDF/A-2b |
| Verapdf validate 2u | `POST /v1/verapdf/api/validate/2u` | Check a PDF against PDF/A-2u |
| Verapdf validate 3a | `POST /v1/verapdf/api/validate/3a` | Check a PDF against PDF/A-3a |
| Verapdf validate 3b | `POST /v1/verapdf/api/validate/3b` | Check a PDF against PDF/A-3b |
| Verapdf validate 3u | `POST /v1/verapdf/api/validate/3u` | Check a PDF against PDF/A-3u |
| Verapdf validate 4 | `POST /v1/verapdf/api/validate/4` | Check a PDF against PDF/A-4 |
| Verapdf validate 4e | `POST /v1/verapdf/api/validate/4e` | Check a PDF against PDF/A-4e |
| Verapdf validate 4f | `POST /v1/verapdf/api/validate/4f` | Check a PDF against PDF/A-4f |
| Verapdf validate ua1 | `POST /v1/verapdf/api/validate/ua1` | Check a PDF against PDF/UA-1 |
| Verapdf validate ua2 | `POST /v1/verapdf/api/validate/ua2` | Check a PDF against PDF/UA-2 |
| Verapdf validate wt1a | `POST /v1/verapdf/api/validate/wt1a` | Check a PDF against WTPDF 1.0 Accessibility |
| Verapdf validate wt1r | `POST /v1/verapdf/api/validate/wt1r` | Check a PDF against WTPDF 1.0 Reuse |
| Verapdf info | `GET /v1/verapdf/api/info` | Get the veraPDF server's environment |
| Verapdf list profiles | `GET /v1/verapdf/api/profiles` | List veraPDF's validation profiles |
| Verapdf get profile | `GET /v1/verapdf/api/profiles/{profile_id}` | Get one veraPDF validation profile |
| Weasyprint render | `POST /v1/weasyprint/render` | Render an HTML document to a PDF |
| Markitdown convert | `POST /v1/markitdown/convert` | Convert a document to Markdown with MarkItDown |
| Docling convert file | `POST /v1/docling/v1/convert/file` | Convert an uploaded document, waiting up to 50 s (1 credit per PDF page, 10 per other file) |
| Docling convert file async | `POST /v1/docling/v1/convert/file/async` | Queue an uploaded document for conversion (1 credit per PDF page, 10 per other file) |
| Docling convert source | `POST /v1/docling/v1/convert/source` | Convert a document from a URL or base64, waiting up to 50 s (1 credit per PDF page, 10 per other file) |
| Docling convert source async | `POST /v1/docling/v1/convert/source/async` | Queue a document from a URL or base64 for conversion (1 credit per PDF page, 10 per other file) |
| Docling status poll | `GET /v1/docling/v1/status/poll/{task_id}` | Check a conversion |
| Docling result | `GET /v1/docling/v1/result/{task_id}` | Download a conversion's result |

## Connection

The plugin connects to `https://api.pagespool.com` over HTTPS and sends your API key, when you set one, in the `X-API-Key` header; the Dify instance needs outbound network access to that endpoint. API reference: https://pagespool.com/docs

## Source and support

Source repository: https://github.com/pagespool-com/pagespool-integrations/tree/main/dify

Support: https://pagespool.com/support

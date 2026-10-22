# Awesome-PDF-Utilities

# Top PDF Utilities Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Self-Hosted Manipulation, Browser-Side Processing & Privacy-First Workflows*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **PDF Utilities**. These tools handle the unglamorous but essential work around PDFs — merging, splitting, compressing, converting, OCR-ing, signing, and redacting — without forcing you to upload sensitive documents to a stranger's server.

**Examples** include Stirling-PDF, BentoPDF, PDF Arranger, OCRmyPDF, qpdf, CoherentPDF, Smallpdf, Adobe Acrobat Pro, Nitro Pro, and Sejda (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, browser-side processing, and command-line automation — ideal for teams handling contracts, invoices, archives, or anything that shouldn't leave the building just to get split in half.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Adobe Acrobat Pro](https://acrobat.adobe.com/)**  
  **The reference commercial PDF editor** with full editing, OCR, form creation, redaction, and e-signatures. **Standard at $12.99/month or $155.88 annually**; **Pro at $19.99/month**. **Trade-offs**: resource-heavy background processes, subscription lock-in, and cloud dependency for many features. **Best for enterprises standardized on Adobe** needing the most complete editing toolchain.

- **[Smallpdf](https://smallpdf.com/)**  
  **Browser-based PDF utility suite** with merge, split, compress, convert, and e-sign. **Free tier limited to a few tasks per day**; Pro subscription unlocks unlimited use. **Trade-offs**: uploads documents to Smallpdf's servers — unsuitable for confidential material. **Best for quick one-off tasks** on non-sensitive documents.

- **[Sejda PDF](https://www.sejda.com/)**  
  **Browser-based PDF editor and converter** with a generous free tier (3 tasks per hour, 50 MB file limit). **Trade-offs**: desktop version available but the hosted service processes files server-side. **Best for occasional editing** without a subscription.

- **[Nitro Pro](https://www.gonitro.com/)**  
  **Commercial PDF editor** with editing, conversion, OCR, and e-sign. Perpetual and subscription licensing options.

## Open-Source GitHub Projects

- **[Stirling-PDF](https://github.com/Stirling-Tools/Stirling-PDF)**  
  **The most complete self-hosted PDF toolkit** — open-core licensed, **50+ PDF tools in one Docker container** [citation:1][citation:2]. **Every tool you'd expect from Acrobat's utility menu**: merge, split, rotate, reorganize, compress (via qpdf), repair, OCR (via Tesseract), convert to/from images, Word, PowerPoint, HTML, Markdown, and CSV (via LibreOffice), add/remove passwords, watermark, certify/sign, redact, flatten, extract images, and compare two PDFs for text differences [citation:2]. **Pipelines** chain multiple operations into reusable automated workflows, and a **REST API** exposes nearly every tool for programmatic integration [citation:1]. **Privacy by architecture**: files exist only client-side, in server memory during task execution, or temporarily on disk for the task — any downloaded file is deleted from the server by that point [citation:2]. **Deployment**: `docker run -p 8080:8080 docker.stirlingpdf.com/stirlingtools/stirling-pdf` [citation:1]. **Resource requirements**: 2 GB RAM minimum, 4 GB recommended (6 GB for heavy DOCX→PDF conversions) [citation:14]. **UI available in 40+ languages** [citation:1]. **Best for teams wanting a private, self-hosted Acrobat replacement** with the broadest tool coverage in one place.

- **[BentoPDF](https://github.com/alam00000/bentopdf)**  
  **The browser-side privacy-first PDF toolkit** — **130+ tools processing entirely in your browser via WebAssembly**, with files never leaving your device [citation:8]. **Self-hostable via Docker** (`docker run -p 3000:8080 ghcr.io/alam00000/bentopdf-simple:latest`) or any static host (Netlify, Vercel, GitHub Pages, Cloudflare Pages) [citation:8][citation:15]. **No file size caps, no usage limits, no account required** [citation:8]. **Core libraries**: pdf-lib (MIT) for merge/split/rotate/encrypt, pdfjs-dist (Apache 2.0) for rendering, PyMuPDF (AGPL-3.0) for PDF↔Text/Markdown/SVG/DOCX, Ghostscript (AGPL-3.0) for PDF/A, CoherentPDF (AGPL-3.0) for bookmark-preserving merges, Tesseract.js for OCR, and LibreOffice WASM for Office conversions [citation:8]. **Air-gapped support**: an automated script prepares a self-contained bundle for isolated networks [citation:8]. **Licensing**: AGPL-3.0 for open-source projects, or a **$49 one-time commercial license** for proprietary use with no AGPL obligations [citation:8]. **Limitation**: **no direct text editing** — it handles form filling, annotations, and document management, but not editing existing paragraph text [citation:15]. **Best for organizations needing self-hosted PDF processing with zero server-side file exposure** — the architecture means even a compromised server never sees your documents.

- **[PDF Arranger](https://github.com/pdfarranger/pdfarranger)**  
  **The interactive page organizer** — GPL licensed, Python-GTK application that helps merge, split, rotate, crop, and rearrange PDF pages with an intuitive graphical interface [citation:11]. **A front end for pikepdf**, a fork of PDF-Shuffler [citation:11]. **Portable Windows build available** via PortableApps.com (41 MB download, 143 MB installed) [citation:6]. **Best for quick page-level surgery** — reordering scans, removing blank pages, splitting a chapter out of a book — without a full PDF editor.

- **[OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF)**  
  **The OCR standard for scanned PDFs** — MPL-2.0 licensed. **Adds a searchable text layer to scanned PDFs**, outputting PDF/A files suitable for archival [citation:7]. **Supports 100+ languages** via Tesseract language packs, **deskew and rotation correction**, **multi-core parallel processing**, **lossless OCR layer injection**, and **image optimization** [citation:7]. **CLI-compatible with upstream OCRmyPDF** (`ocrmypdf -l chi_sim+eng --deskew input.pdf output.pdf`) [citation:7]. **Best for making scanned archives searchable** — the tool to run before any text extraction or RAG pipeline touches a scanned document.

- **[qpdf](https://github.com/qpdf/qpdf)**  
  **The command-line PDF transformation engine** — Apache-2.0 licensed (Artistic-2.0 for older versions) [citation:5]. **Structural transformations**: encryption/decryption, linearization for fast web view, splitting/merging, and PDF-to-PDF transformations that preserve content streams [citation:5]. **Powers Stirling-PDF's compression** and many other tools [citation:2]. **Native crypto implementation** with optional GnuTLS or OpenSSL providers [citation:5]. **Best for scripting PDF structural operations** where you want a focused Unix-style tool rather than a GUI.

- **[CoherentPDF (cpdf)](https://www.coherentpdf.com/)**  
  **The commercial-grade command-line PDF toolkit with an AGPL option** — **free under AGPL** for compliant open-source projects, or commercial license for proprietary use [citation:9]. **Imposition operations** like two-up stacking (`-twoup-stack`), plus merging, splitting, stamping, and content scaling [citation:4]. **Powers BentoPDF's bookmark-preserving merges and PDF↔JSON conversions** [citation:8]. **Best for advanced imposition and scripting** where qpdf's structural focus isn't enough and you need layout-aware operations.

### Additional Strong Open-Source Options

- **PyMuPDF (fitz)** — High-performance PDF library with rendering, text extraction, and manipulation. AGPL-3.0 or commercial license. Powers BentoPDF's conversion tools [citation:8].
- **pdf-lib** — JavaScript library for creating and modifying PDFs in any JavaScript environment. MIT licensed. Powers BentoPDF's core manipulation [citation:8].
- **pikepdf** — Python library for reading and writing PDFs, built on qpdf. The engine behind PDF Arranger [citation:11].
- **Ghostscript** — The classic PostScript/PDF interpreter and converter. AGPL-3.0. Powers PDF/A conversion and rasterization in many tools [citation:8].
- **Tesseract** — The open-source OCR engine underlying OCRmyPDF and Stirling-PDF's OCR [citation:2][citation:7].

**Frameworks for building custom systems**: Combine **Stirling-PDF** for a self-hosted web UI covering 50+ operations with pipelines and API access, **BentoPDF** for browser-side processing where files never touch a server, **PDF Arranger** for interactive page reordering, **OCRmyPDF** for making scanned archives searchable, and **qpdf** or **CoherentPDF** for scripting structural transformations — to build a PDF utility stack tailored to your privacy requirements, document sensitivity, and automation needs.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- PDF utilities differ significantly in deployment model, licensing, and data exposure. **Stirling-PDF processes files server-side** (though deletes them after task completion) — suitable for self-hosted infrastructure you control, not for shared hosting [citation:2]. **BentoPDF processes entirely in your browser** — the server never sees file contents, making it the safer choice for truly sensitive documents [citation:8][citation:15]. **BentoPDF does not edit existing text** — it handles forms, annotations, and document management [citation:15]. **CoherentPDF is AGPL or commercial** — proprietary use requires a paid license [citation:9]. **Adobe Acrobat's subscription runs $12.99–$19.99/month** with resource-heavy background processes. **OCR quality depends on scan quality and language packs** — always review OCR output before archiving.
- Self-hosted open-source solutions require proper resource allocation (Stirling-PDF needs 4 GB RAM for comfortable use), backup of any persistent configuration, and awareness that OCR of large archives is CPU-intensive.

---

**Made for teams and individuals handling PDFs without handing them to a stranger's server.**
Let's make PDF utilities more open, privacy-preserving, and self-hostable.

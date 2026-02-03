# Automated CV & Portfolio Pipeline

This repository serves as a single source of truth for my professional identity. It leverages **CI/CD automation** to generate and deploy both my web portfolio and my LaTeX-based CV.

## 🚀 How it Works

The entire workflow is driven by **GitHub Actions** and triggered by changes in the `data/cv.yaml` file:

1.  **Data Source**: All content is stored in a structured `cv.yaml` file.
2.  **HTML Generation**: A workflow uses **Pandoc** and a custom HTML5/CSS3 template to build a responsive web portfolio, which is then deployed to [lorenzodortona.com](https://lorenzodortona.com) via Cloudflare Pages.
3.  **PDF Generation**: A secondary workflow uses **Pandoc** with the **Tectonic** typesetting engine to compile a professional PDF from a LaTeX template.
4.  **Automated Deployment**: The generated artifacts (HTML and PDF) are automatically updated and committed back to the repository or deployed to production.

## 🛠️ Technical Stack

* **Logic**: YAML (Structured Data)
* **Engines**: [Pandoc](https://pandoc.org/) (Document Converter), [Tectonic](https://tectonic-typesetting.github.io/) (Modern LaTeX)
* **Automation**: GitHub Actions (Workflows)
* **Hosting**: Cloudflare Pages
* **Templates**: Custom HTML/CSS and LaTeX templates

## 📂 Structure

- `data/cv.yaml`: The source of truth for all my information.
- `templates/`: Contains the `site.html` and `cv.latex` templates.
- `.github/workflows/`: Automation logic for building and deploying.
- `index.html` & `cv.pdf`: Generated outputs (automatically updated).

## 🔨 Local Usage

If you have Pandoc and Tectonic installed, you can build the outputs locally:

```bash
# Build HTML
pandoc --template templates/site.html --metadata-file data/cv.yaml -f markdown -t html -o index.html

# Build PDF
pandoc --template templates/cv.latex --metadata-file data/cv.yaml --pdf-engine=tectonic -o cv.pdf
```

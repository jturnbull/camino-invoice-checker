# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-page HTML application for Camino Communications Ltd, a UK-based medical communications agency. The application validates invoices against purchase orders using Claude AI's document analysis capabilities.

## Architecture

- **Single-page application**: All functionality is contained in `index.html`
- **Frontend-only**: Pure HTML, CSS, and JavaScript with no build process
- **AI Integration**: Uses Claude API directly from the browser to analyze PDF documents
- **Document Processing**: Converts PDFs to base64 and sends to Claude for extraction and validation

## Key Components

### Document Validation Logic
The application performs 7 specific validation checks:
1. Job number and description matching
2. PO number verification
3. Billing address validation
4. Currency matching
5. VAT application rules (UK: 20% VAT, non-UK B2B: zero-rated)
6. Payment terms consistency
7. Bank details verification (currency-specific bank accounts)

### Banking Rules
- USD payments: Wise account in Woodhaven, NY
- EUR payments: Wise account in Brussels  
- GBP payments: Allica Bank account in London
- Other currencies: Manual verification required

### VAT Rules for B2B Services
- UK clients: Must charge 20% VAT
- All non-UK business clients (including EU): Zero-rated VAT

## Development

Since this is a static HTML file with no build process:
- Open `index.html` directly in a browser for testing
- All changes are made directly to the HTML file
- No package manager, build tools, or dependencies
- Uses Claude API with CORS headers for browser access

## API Integration

The application makes direct API calls to Claude (Anthropic) using:
- Model: `claude-sonnet-4-20250514`
- PDF processing capability via base64 encoding
- Two-stage process: extraction then comparison
- Requires user-provided API key

## File Structure

```
camino-invoice-checker/
├── index.html          # Complete application (HTML, CSS, JS)
└── .git/              # Git repository
```

No additional configuration files, package managers, or build tools are used in this project.
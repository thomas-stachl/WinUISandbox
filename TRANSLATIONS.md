# Translation Setup

## Overview
This repository uses the `@elgato/translate` tool to manage translations for WinUI resource files (.resw format).

## Current Status

### ✅ Completed
- Translation infrastructure configured (`translations.config.json`)
- English source file: `Resources/en/Resources.resw` (218 entries)
- German translation file: `Resources/de/Resources.resw` (basic translations for 16 common terms)
- French translation file: `Resources/fr/Resources.resw` (basic translations for 17 common terms)
- GitHub Actions workflow configured for automated translations

### 📝 Translation Coverage

| Language | File | Basic Terms | Requires Full Translation |
|----------|------|-------------|---------------------------|
| English (source) | `Resources/en/Resources.resw` | 218 entries | N/A (source) |
| German | `Resources/de/Resources.resw` | 16 translated | 202 entries |
| French | `Resources/fr/Resources.resw` | 17 translated | 201 entries |

## How to Complete Translations

### Option 1: Using the @elgato/translate Tool (Recommended)

The repository includes the `@elgato/translate` npm package which uses DeepL for professional translations.

```bash
# Install the tool
npm install -g @elgato/translate

# Run translations with your DeepL API key
translate -k YOUR_DEEPL_AUTH_KEY
```

This will automatically translate all entries from English to German and French using DeepL's translation service.

### Option 2: Using GitHub Actions (Automated)

The repository includes a GitHub Actions workflow (`.github/workflows/copilot-automation.yaml`) that:
1. Triggers when an issue is created and assigned to @copilot
2. Installs the translation tool
3. Runs translations using the `DEEPL_AUTH_KEY` secret
4. Creates a pull request with the translations

To use this:
1. Ensure the `DEEPL_AUTH_KEY` secret is configured in GitHub repository settings
2. Create or label an issue
3. The workflow will automatically generate translations

### Option 3: Manual Translation

For manual translations, edit the `.resw` files directly:
1. Open `Resources/de/Resources.resw` or `Resources/fr/Resources.resw`
2. Find the `<data>` elements
3. Update the `<value>` elements with translations
4. Maintain the XML structure and `xml:space="preserve"` attributes

## File Structure

```
Resources/
├── en/
│   └── Resources.resw  (Source: English)
├── de/
│   └── Resources.resw  (Target: German)
└── fr/
    └── Resources.resw  (Target: French)
```

## Configuration

The `translations.config.json` file defines:
- **source**: English resource file path
- **targets**: Array of target languages with language codes and output paths

## Notes

- The resource files use Microsoft's RESW format (XML-based)
- Format strings (e.g., `{0}`, `{1}`) must be preserved in translations
- The `xml:space="preserve"` attribute maintains whitespace
- Currently, basic UI terms have been translated; technical/specialized content requires professional translation

## Next Steps

1. Obtain a DeepL API key (free tier available at https://www.deepl.com/pro-api)
2. Run `translate -k YOUR_KEY` to complete all translations
3. Review and verify translations with native speakers
4. Test the application with each language

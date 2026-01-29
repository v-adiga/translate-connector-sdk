# @v-adiga/translate-connector-sdk

This package exports type definitions to build translate connectors.

## Installation

```bash
npm install @v-adiga/translate-connector-sdk
```

## Usage

### Import Translation Types

```typescript
import {
  TranslationRequest,
  TranslationResponse,
  TranslationItem,
  TranslationMessage,
  Locale,
  LocaleCode,
  LocalesResponse
} from '@v-adiga/translate-connector-sdk';

// Example: Type your translation request
const request: TranslationRequest = {
  sourceLocale: 'en-US',
  targetLocales: ['es-ES', 'fr-FR'],
  items: [
    {
      id: 'item1',
      messages: [
        { id: 'msg1', value: 'Hello World' }
      ]
    }
  ]
};

// Example: Type your translation response
const response: TranslationResponse = {
  status: 200,
  results: {
    'es-ES': [
      {
        id: 'item1',
        messages: [
          { id: 'msg1', value: 'Hola Mundo' }
        ]
      }
    ]
  }
};

// Example: Type your locales response
const localesResponse: LocalesResponse = {
  locales: [
    { code: 'en-US', label: 'English (United States)' },
    { code: 'es-ES', label: 'Spanish (Spain)' }
  ]
};
```

## API

### Translation Types

- **`TranslationRequest`** - Request payload for translation
  - `sourceLocale: string` - Source language locale
  - `targetLocales: string[]` - Target language locales
  - `items: TranslationItem[]` - Items to translate

- **`TranslationResponse`** - Response from translation service
  - `status: number` - HTTP status code
  - `error?: string` - Optional error message
  - `results: Record<string, TranslationItem[]>` - Translation results by locale

- **`TranslationItem`** - Single translatable item
  - `id: string` - Unique identifier
  - `messages: TranslationMessage[]` - Messages to translate

- **`TranslationMessage`** - Individual message
  - `id: string` - Message identifier
  - `value: string` - Message content

### Locale Types

- **`LocaleCode`** - Valid locale code (validated by Zod schema)
- **`Locale`** - Locale information
  - `code: LocaleCode` - Locale code
  - `label: string` - Human-readable label

- **`LocalesResponse`** - Response containing supported locales
  - `locales: Locale[]` - Array of supported locales

## Development

### Build

```bash
npm run build
```

This generates TypeScript declaration files (`.d.ts`) in the `dist/` folder.

## License

MIT


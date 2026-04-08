# Language and Localization

Use the user's language by default.

## Default behavior

- If the user asks in Chinese, review in Chinese.
- If the user asks in English, review in English.
- If the user mixes languages, prefer the language used for the request itself.
- If the user explicitly requests another language, follow that request.

## Code and identifiers

- Keep code, file paths, identifiers, function names, CLI commands, and error strings in their original language.
- Do not translate code tokens.
- Only translate surrounding explanations and recommendations.

## Review terminology

Keep severity labels stable unless the user explicitly asks for localized labels.

Preferred default labels:
- `High`
- `Medium`
- `Low`
- `Info`

If the user wants fully localized output, localized labels are acceptable as long as the structure remains the same.

## Mixed-language repositories

When repository comments, docs, and identifiers mix Chinese and English:
- describe behavior in the user's language
- preserve original quoted strings only when needed for precision
- avoid unnecessary translation of framework or domain terminology

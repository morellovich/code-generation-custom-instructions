## Chrome Extension Specific

- Use Manifest V3 standards
- Implement proper message passing between components:
  ```typescript
  interface MessagePayload {
    type: string;
    data: unknown;
  }
  ```
- Handle permissions properly in manifest.json
- Use chrome.storage.local for persistent data
- Implement proper error boundaries and fallbacks
- Use lib/storage for storage related logic
- For the async injected scripts in content/,
  - they must not close over variables from the outer scope
  - they must not use imported functions from the outer scope
  - they must have wrapped error handling so the error message is returned to the caller

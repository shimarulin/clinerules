## Brief overview
This set of guidelines establishes mandatory integration of Context7 MCP tools for all code-related development tasks, ensuring automatic access to library documentation and best practices without explicit user requests.

## Context7 Usage Requirements
- MUST automatically use Context7 MCP tools when working with code generation, setup, or configuration steps
- MUST use resolve-library-id tool to obtain Context7-compatible library IDs before accessing documentation
- MUST use get-library-docs for library and API documentation without requiring explicit user prompts
- SHOULD specify appropriate mode parameter ('code' for API references and code examples, 'info' for conceptual guides) when using get-library-docs
- MAY use pagination parameters (page) when initial documentation results are insufficient

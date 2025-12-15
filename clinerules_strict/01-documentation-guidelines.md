## Brief Overview
This document provides general guidelines for using RFC 2119 keywords in technical documentation. It establishes standards for employing these keywords to ensure precise and consistent communication of requirements, recommendations, and options across project documentation.

## RFC 2119 Keywords
- **"MUST"**, **"MUST NOT"**, **"REQUIRED"**, **"SHALL"**, **"SHALL NOT"** indicate absolute requirements or prohibitions that must be followed.
- **"SHOULD"**, **"SHOULD NOT"**, **"RECOMMENDED"**, **"NOT RECOMMENDED"** indicate recommendations that may be ignored only after careful consideration of the implications.
- **"MAY"**, **"OPTIONAL"** indicate features that are truly optional and may or may not be implemented depending on specific needs.

## Usage Rules
- RFC 2119 keywords are written in **UPPERCASE** to indicate their special, normative meaning.
- When these words appear in **lowercase**, they carry their normal, conversational English meaning.
- When introducing these guidelines in any documentation, always reference RFC 2119.

## Reference
The keywords **"MUST"**, **"MUST NOT"**, **"REQUIRED"**, **"SHALL"**, **"SHALL NOT"**, **"SHOULD"**, **"SHOULD NOT"**, **"RECOMMENDED"**, **"MAY"**, and **"OPTIONAL"** in documentation are to be interpreted as described in [RFC 2119: Key words for use in RFCs to Indicate Requirement Levels](http://www.ietf.org/rfc/rfc2119.txt).

## Examples
- **Correct (Normative):** "The configuration file MUST be in JSON format."
- **Incorrect (Normative intent, but casual):** "You must update the dependencies." (Use **"SHOULD"** or rephrase if it is not an absolute requirement.)
- **Optional Feature:** "The user interface MAY include dark mode support."

## Language Requirement
All project documentation (README files, code comments, API documentation, etc.) MUST be written in English to maintain consistency and broad accessibility.

# Module loaded twice bug

## What happens

A module is executed twice when:
- The HTML is loaded on a url with user info
- The initial HTML contains a script that import a module
- This module is also imported by another script

The bug doesn't appear on Firefox (120.1) Safari (16.6)

## Reproduction

- `npx vite preview` -> one div
- Update the url to `foo:bar@localhost:4137` -> two divs

If the import is not in the HMTL:

- `cd dist && npx vite dev` -> one div
- Update the url to `foo:bar@localhost:5137` -> one div

This is because Vite rewrite the `<script>` into a poxy script that does the import 

# Case Studies and Notes for Zane Riley's Product Design Portfolio

This repository contains the case studies and notes for my product design portfolio. It's a companion to my [main portfolio repository](https://github.com/zaneriley/personal-site), which houses the actual website code, and [the gitops infra](https://github.com/zaneriley/personal-site-infra) that deploys it.

This is to keep my content separate from the application code. In the past, updating my portfolio has a huge pain because it required extracting old content and integrating it into the new design. I hope to keep and preserve published content here, separate from the actual display of the content. 

## Features

- Encryption and decryption helpers for draft files
- Decryption of files for editing
- Pre-commit and pre-push checks for unencrypted drafts
- CI validation against the portfolio app before content can publish

## Content Structure

- `/case-studies`: Markdown for each case study
- `/notes`: Markdown for other writings

## Usage

### Editing Content

1. Decrypt draft files:
   ```
   ./run decrypt
   ```

2. Edit your content files. Mark drafts with `is_draft: true` in the frontmatter.

3. Encrypt drafts before committing:
   ```
   ./run encrypt
   ```

4. Commit and push your changes. The pre-commit and pre-push hooks block if any `is_draft: true` Markdown is still unencrypted.

### Available Commands

- Encrypt all drafts:
  ```
  ./run encrypt
  ```

- Decrypt all encrypted files:
  ```
  ./run decrypt
  ```

- Check for unencrypted drafts:
  ```
  ./run check_unencrypted
  ```

- Prove the scanner, pre-push hook wiring, and CI validation command all block plaintext drafts:
  ```
  ./run ci:draft-safety /path/to/personal-site
  ```

- Validate this content tree against the portfolio app:
  ```
  ./run ci:validate /path/to/personal-site
  ```

## Publishing Safety

Local hooks are authoring guardrails. They catch unencrypted drafts before push, but they are not the remote guarantee.

CI is the publishing boundary. Content validation checks for unencrypted drafts and asks the portfolio app whether the current content tree can parse, validate, compile, and publish. Bad content should fail in the content repo before the production webhook ever sees it.

## Renames

When renaming a published note or case study, add the old slug to the new file's `aliases:` frontmatter. The portfolio app uses that explicit signal to 301-redirect the old URL to the new canonical URL. A pure deletion without an alias keeps the app's hard-404 behavior.

Alias conflicts fail validation. Two live files of the same content type cannot claim the same alias, and an alias cannot conflict with another live canonical slug.

## Security Considerations

- The encryption uses OpenSSL's AES-256-CBC with PBKDF2 for key derivation.
- The encryption key is stored in a `.env` file, which is not committed to the repository.
- Pre-commit and pre-push hooks block unencrypted draft Markdown before push.
- CI repeats the draft-safety check so the remote repository can be made public without relying only on local hook installation.

## Setup

1. Clone this repository:
   ```
   git clone <repository-url>
   ```

2. Create a `.env` file in the project root with your encryption key:
   ```
   ENCRYPTION_KEY=your_secure_encryption_key_here
   ```

3. Make the `run` script executable:
   ```
   chmod +x run
   ```

4. Install lefthook for Git hooks management:
   ```
   lefthook install
   ```


## Contact

You can find more about me and my work at [zaneriley.com](https://zaneriley.com).

---

For more information about the portfolio website itself, please visit the [main portfolio repository](https://github.com/zaneriley/personal-site) and the [gitops infra](https://github.com/zaneriley/personal-site-infra).

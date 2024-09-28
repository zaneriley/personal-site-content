# Case Studies and Notes for Zane Riley's Product Design Portfolio

This repository contains the case studies and notes for my product design portfolio. It's a companion to my [main portfolio repository](https://github.com/zaneriley/personal-site), which houses the actual website code, and [the gitops infra](https://github.com/zaneriley/personal-site-infra) that deploys it.

This is to keep my content separate from the application code. In the past, updating my portfolio has a huge pain because it required extracting old content and integrating it into the new design. I hope to keep and preserve published content here, separate from the actual display of the content. 

## Features

- Automatic encryption of draft files
- Decryption of files for editing
- Pre-commit hook to ensure drafts are encrypted
- Pre-push hook to prevent pushing unencrypted drafts

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

3. Commit your changes. Drafts will be automatically encrypted.

4. Push your changes. The pre-push hook will ensure all drafts are encrypted.

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
  ./run check
  ```

## Security Considerations

- The encryption uses OpenSSL's AES-256-CBC with PBKDF2 for key derivation.
- The encryption key is stored in a `.env` file, which is not committed to the repository.
- Pre-commit and pre-push hooks ensure that drafts are always encrypted before being pushed to the remote repository.

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
# CaptionBough — proposed AWS architecture

CaptionBough uses AWS speech, translation and generative AI services to turn authorised recordings into accurate, editable, multilingual captions.

## Request flow

1. Video upload
2. Amazon S3
3. Transcribe
4. Translate
5. Bedrock check
6. Reviewer edit
7. Subtitle export

## Services

### Amazon Transcribe

**Role:** Transcribe speech

Converts speech into timed transcripts with speaker labels, using custom vocabularies so names, acronyms and technical terms are recognised correctly.

### Amazon Translate

**Role:** Draft translations

Translates captions into Yoruba, Igbo, Hausa, French and other languages, applying custom terminology so key terms stay consistent.

### Amazon Bedrock

**Role:** Check terminology and consistency

Compares captions against your glossary and the rest of the transcript, flagging likely misheard words and inconsistent terms for reviewers.

### Amazon S3

**Role:** Store videos and subtitles

Keeps uploaded videos, caption drafts and exports encrypted, with lifecycle rules to remove source videos when you choose.

### AWS Lambda

**Role:** Orchestrate the pipeline

Runs transcription and translation jobs, segments captions, applies style rules and generates exports.

## Principles

- **Authorised content only** — Uploaders confirm they have the right to caption each recording.
- **Humans finish** — Machine drafts, reviewer approval.
- **Your vocabulary** — Custom terms keep captions accurate.

## Safeguards

- **Rights confirmed** — Every upload requires confirmation that you are authorised to caption it.
- **Reviewer approval** — Captions and translations are drafts until a reviewer approves them.
- **Supports accessibility programmes** — CaptionBough helps meet captioning needs; formal compliance assessment stays with your accessibility team.
- **Private recordings** — Videos are encrypted and never used to train shared models.

## MVP scope

Upload a set of authorised training or lecture videos. We generate captions and translations, your reviewers edit them in the browser, and you export subtitles for your platforms.

- Authorised video upload
- Automated transcription
- Caption editor
- Translation into two languages
- SRT / VTT exports

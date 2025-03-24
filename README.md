# Multilingual Glossary API

A Rails JSON API for defining source/target language glossaries, mapping terms, and applying those mappings to submitted text.

## Domain model

```text
Glossary (source language -> target language)
  `-- Terms (source term -> target term)

source text + glossary -> translated/replaced text response
```

## Core routes

- `POST /glossaries`, `GET /glossaries`, `GET /glossaries/:id`
- `POST /glossaries/:glossary_id/terms`
- `POST /translations`

Example glossary:

```json
{"glossary":{"source_language_code":"en","target_language_code":"es"}}
```

## Local setup

```bash
bundle install
rails db:create db:migrate
rails server
```

PostgreSQL configuration should be provided through the environment expected by `config/database.yml`. Docker Compose is included, but setup should not require editing framework source files; document local overrides outside committed application code.

## Verification boundaries

Model and environment specs are present. Translation is glossary-term replacement, not a statistical or generative translation system. Authentication, authorization, matching precedence, punctuation/case behavior, and large-glossary performance require further validation.

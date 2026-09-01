# ER Diagram

```mermaid
erDiagram

    USER ||--o{ APPLICATION : has_many
    COMPANY ||--o{ APPLICATION : has_many
    APPLICATION ||--o{ INTERVIEW : has_many
    APPLICATION ||--o| REJECTION_REASON : has_one
    APPLICATION ||--o| JOB_POSTING_RAW_TEXT : has_one

    USER {
        bigint id PK
        string email
        string encrypted_password
        datetime created_at
        datetime updated_at
    }

    COMPANY {
        bigint id PK
        string name
        string normalized_name
        text note
        datetime created_at
        datetime updated_at
    }

    APPLICATION {
        bigint id PK
        bigint user_id FK
        bigint company_id FK
        string job_title
        string job_url
        string job_site
        string location
        string salary
        string employment_type
        date applied_on
        string application_method
        integer status
        text note
        datetime created_at
        datetime updated_at
    }

    INTERVIEW {
        bigint id PK
        bigint application_id FK
        date interview_date
        string stage
        string format
        text questions
        text answers
        text impression
        string result
        text note
        datetime created_at
        datetime updated_at
    }

    REJECTION_REASON {
        bigint id PK
        bigint application_id FK
        string category
        text detail
        datetime created_at
        datetime updated_at
    }

    JOB_POSTING_RAW_TEXT {
        bigint id PK
        bigint application_id FK
        text raw_text
        datetime created_at
        datetime updated_at
    }
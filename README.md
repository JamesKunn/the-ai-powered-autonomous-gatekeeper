graph TD
    A[🌐 GitHub Pages Form] -->|JSON POST| B[⚡ Zapier Webhook]
    B --> C{🤖 OpenAI Brain}
    C -->|Analyze & Score| D[🛠️ Data Formatter]
    D --> E{Score Filter}
    
    E -->|Score > 7| F[📅 Google Calendar]
    F --> G[📧 Gmail Confirmation]
    
    E -->|Score < 7| H[📱 Telegram Bot]
    H --> I[📡 Low-Prio Channel]
    
    style C fill:#f9f,stroke:#333,stroke-width:2px
    style A fill:#bbf,stroke:#333,stroke-width:2px
    style G fill:#dfd,stroke:#333,stroke-width:2px
    style I fill:#ffd,stroke:#333,stroke-width:2px

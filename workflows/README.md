# ShopLina WhatsApp workflow backup

Captured from the n8n editor on 4 October 2026. Contains all 23 selected nodes and their connections, including existing unconnected experimental audio nodes.

## Runtime

n8n remains the runtime on the existing server. This GitHub backup does not host n8n, receive WhatsApp webhooks, or replace Oracle Cloud. No GitHub Actions schedule or automatic deployment is configured.

## Backup scope

shoplina-whatsapp.json is a sanitized, inactive importable node configuration, obtained through the editor's Copy nodes command. It is not a full instance/database backup. It excludes saved credentials and their IDs/names, pinned examples, instance metadata, execution history, conversation/static data, and original webhook path. Original workflow-level settings were not exported; the backup uses executionOrder v1 and must be checked on restore.

Existing node logic and connections are preserved. This backup does not implement human takeover or Facebook/TikTok/YouTube publishing. Current reply logic requests text replies and up to four product images when requested. Legacy audio branches remain included for fidelity.

## Restore to a separate test workflow

1. Import the JSON into n8n as a new inactive workflow.
2. Assign saved OpenAI credentials to the model, transcription and legacy audio nodes.
3. Assign YCloud header-auth credentials to HTTP Request1, HTTP Request2, HTTP Request4, HTTP Request5 and HTTP Request6.
4. Only if needed, assign Gemini credentials to the disconnected Gemini experiment and verify its configuration.
5. The webhook path is shoplina-whatsapp-restore. Use a separate test sender; do not replace the production webhook during testing.
6. Check workflow settings, product endpoint, node versions and permissions. Test text, transcription, photos and order links with a test recipient before publishing.

Keep API keys inside n8n's credential store. Never commit credentials, production webhook secrets, customer messages, phone numbers or database exports to this public repository.

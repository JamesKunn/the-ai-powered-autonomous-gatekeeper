# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

This is a static website project with no build process:
- To view the site: Open `index.html` in a web browser
- To develop: Edit `index.html` directly and refresh the browser
- No npm dependencies, build tools, or test framework are configured

## Code Architecture

### High-Level Structure
- **Frontend**: Single `index.html` file containing HTML, CSS (Tailwind via CDN), and JavaScript
- **Backend Integration**: Form submits directly to Zapier webhook (`https://hooks.zapier.com/hooks/catch/26397280/uesn8ky/`)
- **AI Processing**: Zapier forwards data to OpenAI for analysis and scoring (as shown in README flowchart)
- **Routing Logic**: Based on OpenAI score (>7 or <7), leads are routed to:
  - High score: Google Calendar + Gmail confirmation
  - Low score: Telegram bot + low-priority channel

### Key Files
- `index.html`: Main application file containing:
  - Form with name, email, and message fields
  - Tailwind CSS styling via CDN
  - JavaScript handling form submission, loading states, and UI feedback
  - Zapier webhook integration (replace URL in script with actual endpoint)

### Data Flow
1. User fills form in browser
2. JavaScript prevents default submit, shows loading state
3. Form data sent via POST to Zapier webhook (no-cors mode)
4. Zapier triggers OpenAI analysis workflow (per README flowchart)
5. Based on score, routes to appropriate channels
6. UI shows success/error messages and resets form

## Common Tasks

### Updating the Zapier Webhook
1. Locate the fetch URL in index.html line ~82
2. Replace `https://hooks.zapier.com/hooks/catch/26397280/uesn8ky/` with your actual webhook endpoint
3. Ensure the webhook accepts JSON payload with name, email, message fields

### Modifying Form Fields
1. Edit the HTML form elements in index.html
2. Update corresponding JavaScript data collection (lines 74-78)
3. Ensure Zapier webhook expects the updated field names

### Styling Changes
- Tailwind CSS is loaded via CDN in the head
- Custom CSS is in the `<style>` tag
- Modify classes directly in HTML or add new styles to the style block

## Environment Configuration
This project uses OpenRouter for AI model access via Claude Code:
- Settings are in `.claude/settings.local.json`
- Configured to use nvidia/nemotron-3-super-120b-a12b:free for all model types
- API base URL: https://openrouter.ai/api
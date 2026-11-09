# Visibly AI CMS Connector

Die gemeinsamen Arbeits- und Integrationshinweise stehen in [AGENTS.md](AGENTS.md).
Vor Änderungen den dort verlinkten Zusammenhang zwischen MCP, Plattform,
CMS-SDK und anyCMS-Anwendungsfällen lesen.

## Connector-Sync (Pflicht, seit 09.11.2026)

Diese Repos bilden zusammen eine Schnittstelle und werden immer gemeinsam nachgezogen:

- `visibly-app`: Pull-API (`backend/app/routers/content/pull_api_routes.py`), Webhook-Payload, Confirm-Endpunkt.
- `visibly-ai-cms-connector`: öffentliches SDK (`ai_content_autopilot`). Die Feldtabelle im README ist der Vertrag.
- `visiblyai`: Blog-Connector der Marketingseite. Nutzt das SDK; eigene Logik nur für Datei, Rückprüfung und GitHub-Commit.
- `visiblyai-mcp-server`: Artikel-, Draft- und Live-URL-Werkzeuge mit derselben Feldsemantik.
- `anycms`: Beispiele (WordPress, Astro, Next.js, Flask) auf der aktuellen SDK-Version.

Ändert sich in einem Repo ein Feld, ein Statuscode, die Webhook-Signatur oder ein Endpunkt, im selben Zug die anderen
prüfen und nachziehen, je Repo mit Test und CHANGELOG-Eintrag. Anlass: Am 09.11.2026 scheiterte der erste Blogartikel
an `missing_language`, weil Pull-API, SDK-Doku und Marketing-Connector auseinandergelaufen waren.

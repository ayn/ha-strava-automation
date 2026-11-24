# Agent-assisted setup

Strava Automation is an independent integration, domain `ha_strava_automation`.
Use HA MCP's installed tools and best-practice guide. Installing this component
alone does not grant permission to enable writes or change real activities.

1. Discover existing integrations, accounts, application credentials, automations
   and dashboards. Ask only for details the connected instance cannot supply.
   Do not assume the first athlete is the intended one. Do not return tokens,
   app secrets, full webhook URLs or private activity bodies in tool output.
2. Check the HA version, Marketplace/HACS state and recovery backup. Use a
   versioned release/custom repository; complete store notices in the user's UI.
   Downloading does not prove the runtime loaded; restart when required.
3. For a new connection, use native Application Credentials and the integration's
   config flow. The user completes Strava browser consent. Verify the resulting
   account identity and scopes. Read consent is required; writes/profile are
   optional. Keep preview enabled until the user authorizes a live rule.
4. For another installed provider, choose a separate API app for coexistence, or
   follow the [manual migration guide](MIGRATION.md). The user manages the old
   integration and completes fresh Strava consent through native HA setup.
5. Check public HTTPS webhook access, including validation GET and event POST.
   Ordinary private VPN access is insufficient. Do not expose unrelated HA paths
   or weaken an entire reverse-proxy policy to allow one callback.
6. Import the selected blueprint and choose this account. Select a training calendar
   for workout classification and a shoe from its own gear catalog if requested.
   Keep per-rule dry_run and integration Preview only enabled for initial checks.
7. Preview a real owned activity without writing. Verify account isolation,
   expected changes, separate history streams and retained job receipts. Do not
   inject synthetic activity-ready events into a live automation as a test.
8. If authorized, enable the chosen rules and integration writes. Short-run muting
   should consume `ha_strava_automation_workout_processed` after classification,
   rather than racing `ha_strava_automation_activity_ready`. Other mute rules can
   process normal activity-ready events. Preserve unrelated automations.
9. Help the user see results using Latest preview / Latest run, the native example
   card, action responses, job status and notifications. No dashboard is installed
   automatically. Raw activity data is not appropriate for public screenshots.
10. Report installed version, restart result, account/rule state, receipt comparison
    and remaining user steps. Repository installation does not imply default-store
    listing. State test baseline and live validation separately.

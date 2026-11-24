# Switch to Strava Automation

Strava Automation connects through its own Home Assistant Application
Credentials and Strava consent flow. The procedure below applies when replacing
another Strava integration or the older Strava Activity Tools companion.

1. Review the old integration's automations, dashboards and external listeners.
   Save the settings you want to recreate, including filters, calendar selection
   and shoe choices. Let pending jobs finish before disabling old automations.
2. Choose the Strava API app for Strava Automation. Use a separate app if the old
   integration will stay connected. Strava permits one webhook subscription per
   API app.
3. If you are reusing the existing API app, remove the old integration yourself
   through Home Assistant and confirm that its webhook subscription has been
   removed through the old integration or Strava's documented
   [subscription management](https://developers.strava.com/docs/webhooks/).
4. Follow the [installation steps](../README.md#install-and-connect). In Strava
   Automation, enter the app credentials and complete fresh consent.
   If setup reports a subscription conflict, check the callback in the old
   integration or Strava before retrying.
5. Point automations, dashboards and listeners at the new entry's entities,
   actions and [events](../README.md#native-actions-and-events). Review the new
   rules in preview mode before enabling writes. Activity Tools jobs and history
   stay with the old integration. When the new rules are ready, remove the old
   integration in Home Assistant if you no longer use it.

If Strava Automation already has a working connection, keep the existing entry
when upgrading. The entry keeps its authorization, webhook, options and job
history.

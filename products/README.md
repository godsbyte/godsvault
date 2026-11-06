# products/

One profile per product under test, named `<product>.md`, created from `templates/product-profile.md`.

The QA system is product-agnostic: nothing about a specific application is hardcoded in agents or skills. Everything product-specific (repo paths, environments, stack, test commands, ticket keys) lives here.

Onboarding: the user supplies app URL, repo name/path, and ticket number → supervisor performs read-only discovery → drafts the profile → user confirms. Application repos are accessed read-only and only after approval is recorded in the profile.

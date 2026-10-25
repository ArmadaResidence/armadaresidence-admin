# armadaresidence-admin

Deploy-only repository for the Armada Residence dashboard (**admin.armadaresidence.com**).

The source lives in [`armadaresidence-website/admin`](https://github.com/ArmadaResidence/armadaresidence-website/tree/main/admin).
`.github/workflows/deploy.yml` checks that repository out, builds `admin/` and publishes it to this repository's GitHub Pages site.
Nothing else is kept here.

- Deploy: `gh workflow run deploy.yml -R ArmadaResidence/armadaresidence-admin` (or the website repository's `repository_dispatch` `admin-deploy`).
- Repository variables: `VITE_SUPABASE_URL`, `VITE_SUPABASE_PUBLISHABLE_KEY` (public), `ADMIN_DOMAIN` (set to `admin.armadaresidence.com` once the DNS CNAME exists).
- After every deploy the `verify` job runs the website repository's `scripts/admin-cors-check.mjs`: the dashboard functions (`booking-admin`, `admin-users`) must answer the CORS preflight from the deployed origin and from `admin.armadaresidence.com` and refuse POSTs without a valid token. Red run = the dashboard cannot call its functions; fix the functions (`supabase/functions/_shared/cors.ts`) and redeploy them.

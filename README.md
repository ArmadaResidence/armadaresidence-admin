# armadaresidence-admin

Deploy-only repository for the Armada Residence dashboard (**admin.armadaresidence.com**).

The source lives in [`armadaresidence-website/admin`](https://github.com/ArmadaResidence/armadaresidence-website/tree/main/admin).
`.github/workflows/deploy.yml` checks that repository out, builds `admin/` and publishes it to this repository's GitHub Pages site.
Nothing else is kept here.

- Deploy: `gh workflow run deploy.yml -R ArmadaResidence/armadaresidence-admin` (or the website repository's `repository_dispatch` `admin-deploy`).
- Repository variables: `VITE_SUPABASE_URL`, `VITE_SUPABASE_PUBLISHABLE_KEY` (public), `ADMIN_DOMAIN` (set to `admin.armadaresidence.com` once the DNS CNAME exists).

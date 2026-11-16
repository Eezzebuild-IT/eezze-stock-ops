# Eezzebuild's fork of Stock Ops

Forked 16 Nov 2026 from denzizzy966/stock_ops (`new-develop`, MIT; the original licence stays in `license.txt`) as the
base of the Eezzebuild staff app's stock screens (owner: the free open-source Frappe apps are the base, modified and
improved; eezze-erpnext-app `docs/research/2026-11-16-combine-open-source-frappe-apps.md` §7).

Changed on branch `eezze`, so it can live beside eezze-erpnext's theme on the same site:
- no approval Workflow on Material Request (our branch transfers are Material Requests the hub submits; a workflow
  would refuse them);
- no request-to-pay flow and no hooks on Payment Entry, Journal Entry or Purchase Invoice (approvals and payments are
  eezze-erpnext's; payments are authorised in the bank);
- its roles get no rights on Quotation, no Quotation fields and no Quotation screen; `create_quotation` refuses
  (quoting is the sales team's, eezze-erpnext decision 0050);
- the Request to Pay module is not installed (`modules.txt`): no RTP doctypes, roles or workspace on the site; the
  screen hides its menu because `rtp_caps` reports it off when the doctype is absent;
- English is the default language (`Stock Ops Settings` and the settings API).

Checked on the staging copy (eezze-erpnext `docs/how-to/erpnext-staging.md`): installs beside eezze_erp_theme with
no workflow on Material Request and every Eezze role's Custom DocPerm row unchanged.

Still to adapt: the screen bundle's own fallback language (`frontend/src/lib/i18n.js`, rebuilt into `public/`), the
transfer screens to the hub's `/api/erp/ibt` (countersign, follow-up, signatures, photos), and
its roles mapped onto the Eezze job profiles.

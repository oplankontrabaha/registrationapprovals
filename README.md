# OKB Waterway Registration Approvals

**Live page:** https://oplankontrabaha.github.io/registrationapprovals/

The OKB Secretariat's approval queue. It lists every waterway registration still waiting for a decision and shows each line on a map. From here you can approve, reject, approve under a corrected name, or approve several at once, and build a PDF briefer for the approving authority.

## How it works

- This repository holds only the page (`index.html`). It is served by GitHub Pages.
- The decisions themselves run in the Apps Script project, in `ApprovalQueue.gs` and `WaterwayApprovalBackend`: the same rules, receipt emails and SSOT bridge as the email Approve/Reject links.
- The page calls the Apps Script `/exec` URL (`OKB_API_URL` in `index.html`) with `POST` requests. The body is `text/plain` JSON of the form `{ fn, args }`, answered by `doPost()` in `Code.gs`.

## Sign-in

Use the Secretariat passcode stored in the Apps Script project. To create it the first time, run `OKB_QUEUE_SETUP()` in the editor. To replace it and sign everyone out, run `OKB_QUEUE_NEW_PASSCODE()`. A regional sign-in from the Registration Portal does not open this page.

## Trying the page without the server

Add `?preview=1` to the address. It opens with sample data, and nothing is written.

## Related

- Registration Portal: https://oplankontrabaha.github.io/registration/

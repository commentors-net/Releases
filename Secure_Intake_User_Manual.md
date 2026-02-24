# Secure Intake User Manual (Portal + TokCon)

Last updated: 2026-02-24  
Audience: Admin users, TokCon operators, and support staff

## 1. Purpose

This guide explains how to run the full Secure Intake process from file upload to TokCon processing.

End-to-end flow:

1. Admin uploads file in Secure Intake portal.
2. Backend validates, scans, sanitizes, and marks file `ReadyToPull`.
3. TokCon pulls file content from Secure Intake API.
4. TokCon processes addresses (send/freeze or freeze/unfreeze).
5. TokCon acknowledges processing and file transitions to `Inactive`.

## 2. Roles

`Portal Admin`
- Login with password + authenticator code (TOTP).
- Upload files, view states, edit TXT/CSV content, reauthorize re-pull, manage users, export audit.

`TokCon Operator`
- Pull ready files from Secure Intake in TokCon.
- Run blockchain actions (Bulk Send/Freeze, Bulk Freeze/Unfreeze).

`Support/Ops`
- Maintain backend/frontend availability.
- Keep credentials/config aligned between backend and TokCon.

## 3. File Rules

Accepted intake types:
- `.csv`
- `.txt`
- `.pdf`

TokCon processing types:
- Bulk Send uses `.csv`
- Freeze/Unfreeze uses `.txt`

Recommended CSV format:
```csv
oid,address,amount
1001,0xD52ce605559c404F635D16572144D7873436D530,250
1002,0x79A28044Af136e7AEcCc0783e92Fa07f2aEF2e5C,125
```

TXT format (one address per line):
```txt
0xD52ce605559c404F635D16572144D7873436D530
0x79A28044Af136e7AEcCc0783e92Fa07f2aEF2e5C
```

## 4. Portal Login and 2FA

### 4.1 First Login

1. Open the Secure Intake frontend.
2. Enter username/password.
3. On first successful password login, QR code and manual key are shown.
4. Scan QR in authenticator app (Google Authenticator, Microsoft Authenticator, etc.).
5. Enter authenticator code and sign in.

### 4.2 Daily Login

1. Enter username/password.
2. Enter current authenticator code.

## 5. Daily Operating Flow

### 5.1 Upload and Prepare (Portal Admin)

1. In **Quick Upload Flow**, choose file.
2. Click **Upload and Prepare for TokCon**.
3. Wait for completion message indicating file is ready.
4. In **Intake Files**, confirm state is `ReadyToPull`.

What happens automatically:
- Intake validation
- Scan step
- Sanitize step
- Transition to `ReadyToPull`

### 5.2 TokCon Bulk Send (CSV)

1. Open TokCon and go to **Bulk Send** tab.
2. Click **Fetch Ready CSV Files**.
3. Select one queue row in grid.
4. Click **Pull Selected CSV File**.
5. Verify addresses/amounts are loaded in grid.
6. Click **Send and Freeze**.
7. Continue clicking **Send and Freeze** until all rows are processed.

Result:
- TokCon acknowledges file.
- Backend transitions file to `Inactive` when processing succeeds.

### 5.3 TokCon Freeze/Unfreeze (TXT)

1. Open TokCon and go to **Freeze/Unfreeze** tab.
2. Click **Fetch Ready TXT Files**.
3. TokCon pulls first ready TXT automatically and displays addresses in grid.
4. Click **Bulk Freeze** or **Bulk Unfreeze**.
5. If retry addresses remain, run again until list is empty.

Result:
- When no pending addresses remain, TokCon acknowledges success.
- Backend transitions file to `Inactive`.

## 6. Review and Edit File Content (Portal Admin)

Use when uploaded TXT/CSV content needs correction before TokCon pull.

1. In **Intake Files**, select the file row.
2. In **File Content Editor**, click **Load Selected Content**.
3. Edit content in textarea.
4. Enter reason in **Edit Reason**.
5. Click **Save and Reprocess**.
6. Wait until file returns to `ReadyToPull`.

Note:
- Only `.txt` and `.csv` are editable.
- Save action re-queues scan/sanitize and revokes active pull leases.

## 7. Reauthorization for Controlled Re-Pull

Use when a previously processed file must be pulled again.

1. Select file in **Intake Files**.
2. Click **Reauthorize Selected** (or use **Advanced File Actions**).
3. Enter clear reason.
4. Confirm file returns to `ReadyToPull`.
5. TokCon can now pull it again.

## 8. Admin User Management (Portal Admin)

In **Admin Users**:

1. `Create`
   - Enter username + password (minimum 12 characters).
   - Click **Create Admin User**.
2. `Update`
   - Select user row.
   - Change username/password/active state.
   - Click **Update Selected User**.
3. `Delete`
   - Select user row.
   - Click **Delete Selected User** and confirm.

Protection rules:
- You cannot delete your own active session user.
- Last active admin cannot be deleted/deactivated.
- Password reset clears TOTP enrollment; user must re-enroll on next login.

## 9. Audit and Retention

### 9.1 Audit Search and Export

1. Open **Audit Search / Export**.
2. Optional filters: `file_id`, `event_type`.
3. Click **Search Audit**.
4. Click **Export CSV** for report download.

### 9.2 Retention Workflow

1. Select file.
2. In **Advanced File Actions**, submit **Request Retention Purge** with reason and ticket.
3. Run **Approve Retention Action** when approval is complete.
4. Optional: enable `Execute Purge Event`.

## 10. File State Meanings

`PendingIntake`  
File record created, not yet quarantined.

`Quarantined`  
Stored in quarantine; waiting for scan.

`Scanned`  
Scan passed; waiting for sanitization.

`Sanitized`  
Sanitize completed.

`ReadyToPull`  
TokCon is allowed to pull.

`Pulled`  
Artifact pulled by TokCon with valid lease.

`Inactive`  
Processing completed and acknowledged.

`Rejected`  
Blocked by validation/scan/sanitize policy.

## 11. Troubleshooting

`Problem: Bulk buttons disabled in TokCon`
- Cause: No TXT content loaded or list empty.
- Fix:
  1. Click **Fetch Ready TXT Files**.
  2. Verify addresses appear in grid.
  3. Retry if queue empty.

## 12. Operator Do/Do-Not Rules

Do:
- Use portal upload only for new intake files.
- Keep clear reasons for edits and reauthorizations.
- Confirm file reaches `Inactive` after processing.
- Use audit export for compliance evidence.

Do not:
- Manually open untrusted files on TokCon host.
- Share service credentials in chat/email.
- Use DB manual edits for normal lifecycle actions.

## 13. End-to-End Acceptance Checklist (Practical)

1. Login to portal with 2FA works.
2. Upload CSV and file reaches `ReadyToPull`.
3. TokCon pulls CSV, processes, and ack transitions file to `Inactive`.
4. Upload TXT and TokCon displays addresses (not file ids) in grid.
5. Bulk Freeze/Unfreeze runs and ack completes.
6. Reauthorize returns file to `ReadyToPull`.
7. Audit search/export shows lifecycle events.
8. User CRUD works (create/update/delete with guardrails).

If all 8 checks pass, the secure intake user flow is operational.

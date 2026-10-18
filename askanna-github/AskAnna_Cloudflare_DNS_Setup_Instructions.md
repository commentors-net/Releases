# AskAnna — Cloudflare DNS Setup Request

**Prepared for:** AskAnna owner / Cloudflare administrator  
**Priority:** Needed before the five new LIVE/TEST web addresses can be publicly accessed

## 1. What we are doing and why

We are preparing a separate LIVE and TEST deployment of AskAnna on the **existing hosting server**. The aim is to give public visitors, sales/operators, and administrators their own clear web addresses, while allowing testing without replacing the existing live site.

The five new subdomains have **already been created in cPanel/WHM**, but they do not yet resolve on the public internet. The domain `askanna.online` uses Cloudflare as its authoritative DNS provider, so only a person with access to the Cloudflare zone can publish the necessary DNS records.

**This request is only to add DNS records.** It does not require moving the website, changing domain nameservers, deleting existing DNS records, or altering the current production site.

## 2. Planned web addresses

| Purpose | LIVE address | TEST address |
|---|---|---|
| Public-facing AskAnna concierge | `https://askanna.online` (existing) | `https://test.askanna.online` |
| Sales/operator workspace | `https://studio.askanna.online` | `https://teststudio.askanna.online` |
| Existing-customer administration | `https://admin.askanna.online` | `https://testadmin.askanna.online` |

The existing application currently exposes functions through paths such as `/prospects2`, `/prospects2/login`, and `/admin`. The new hostnames will eventually route to their corresponding interfaces once application deployment and routing are completed.

**Important:** Creating DNS records does **not** by itself make those interfaces functional or ready for users. Deployment, host routing, authentication, and HTTPS must also be verified.

## 3. What has already been completed

- The five new subdomains have been created in cPanel, with separate document roots.
- The existing `askanna.online` website remains in place.
- The hosting account `askanna` has AutoSSL enabled.
- Previously excluded new domains were removed from cPanel's AutoSSL exclusion list; verification returned an empty list (`data: []`).
- Public DNS was checked using Cloudflare's public resolver (`1.1.1.1`): `askanna.online` resolves to Cloudflare proxy IPs, while none of the five new subdomains returned a public **A** record.
- The authoritative nameservers were verified as `adaline.ns.cloudflare.com` and `donald.ns.cloudflare.com`.

The five new domains currently have self-signed certificates on the origin server. Trusted HTTPS is **not yet confirmed** for them.

## 4. Action requested from the Cloudflare administrator

### Step A — Confirm the correct origin address

Before adding records, identify the **publicly reachable origin IP address** used by the existing AskAnna hosting server. It must be confirmed from the hosting/network configuration or the existing Cloudflare DNS configuration. **Do not use `192.168.1.151`**, which is a private network IP, and **do not use** the Cloudflare proxy IPs `104.21.60.122` or `172.67.196.71` as the origin IP.

If the current site uses a tunnel, load balancer, reverse proxy, or a CNAME target rather than a directly accessible origin IP, ask the developer to confirm the appropriate DNS target before proceeding. Do not assume an A record is correct in that case.

### Step B — Add five records in Cloudflare

1. Sign in to Cloudflare.
2. Select the zone **`askanna.online`**.
3. Go to **DNS → Records**.
4. Click **Add record** for each entry below.
5. For a directly reachable origin server, use **Type: A**, the names shown below, and the **verified public origin IP** as the Content/IPv4 address.
6. Use **TTL: Auto**.
7. Set **Proxy status: DNS only (grey cloud)** *initially*, provided the origin is reachable directly from the internet and this is permitted by the server's security configuration. This makes origin certificate validation and troubleshooting more straightforward. **DNS only exposes the origin IP**, so do not select it without confirming that this is acceptable.
8. Save each record.

| Type | Name (Cloudflare DNS field) | Content | TTL | Initial proxy setting |
|---|---|---|---|---|
| A | `studio` | **VERIFIED_PUBLIC_ORIGIN_IP** | Auto | DNS only* |
| A | `admin` | **VERIFIED_PUBLIC_ORIGIN_IP** | Auto | DNS only* |
| A | `test` | **VERIFIED_PUBLIC_ORIGIN_IP** | Auto | DNS only* |
| A | `teststudio` | **VERIFIED_PUBLIC_ORIGIN_IP** | Auto | DNS only* |
| A | `testadmin` | **VERIFIED_PUBLIC_ORIGIN_IP** | Auto | DNS only* |

\*If direct access to the origin is blocked or exposing the IP is not acceptable, **do not force DNS only**. Coordinate with the developer on a Cloudflare-proxied setup and certificate validation instead. Cloudflare's HTTP proxy can also affect certificate validation and origin connectivity, so it must be tested.

**Optional `www` hostnames:** cPanel also created `www.studio`, `www.admin`, `www.test`, `www.teststudio`, and `www.testadmin`. These are **not part of the six required URLs** and need not be published now. If they are later required, DNS, SSL, and routing must be configured for them separately. Their absence should not delay the five primary subdomains.

### Step C — Verify public DNS

After saving, confirm that each new hostname resolves to the intended destination. Example from a terminal:

```bash
dig @1.1.1.1 +short A studio.askanna.online
dig @1.1.1.1 +short A admin.askanna.online
dig @1.1.1.1 +short A test.askanna.online
dig @1.1.1.1 +short A teststudio.askanna.online
dig @1.1.1.1 +short A testadmin.askanna.online
```

For **DNS only** A records, each should return the verified origin IP. For **proxied** records, public DNS will normally return Cloudflare IPs instead; that is expected and does not prove the origin is reachable.

### Step D — Inform the developer

Please confirm when the five records are saved, and provide:

- The DNS record target used (origin IP or other target).
- Whether each record is **DNS only** or **Proxied**.
- Any relevant origin firewall, proxy, or Cloudflare access restrictions.

The developer will then run an AutoSSL check for the `askanna` cPanel account, inspect the certificate issuance results, and verify the five HTTPS URLs. If AutoSSL fails, the log will determine the next fix; DNS alone does not guarantee issuance.

## 5. What must NOT be changed

To avoid disruption to the existing production service:

- **Do not change** the existing `askanna.online` DNS record.
- **Do not change** the domain's Cloudflare nameservers.
- **Do not disable** Cloudflare for the main domain.
- **Do not delete or replace** existing MX, SPF, DKIM, DMARC, mail, or other DNS records.
- **Do not change** the existing production SSL certificate or the hosting account's document root.
- **Do not use** `192.168.1.151` or Cloudflare's edge IP addresses as the origin target.
- **Do not add wildcard DNS** (`*`) as a shortcut; use the five explicit records.

## 6. What happens after DNS is configured

The developer will:

1. Confirm public DNS resolution for the five subdomains.
2. Run AutoSSL for the `askanna` account and inspect the log for successful validation and installation.
3. Verify browser-trusted HTTPS on each hostname.
4. Finish/verify LIVE and TEST code deployment and host-based routing.
5. Verify login/access restrictions, operator/admin separation, and that the existing public website still works.
6. Test the intended shared services and ensure TEST actions cannot accidentally send emails to real customers or make unsafe production changes.

**Operational note:** LIVE and TEST are planned as separate code deployments, but the current plan uses the **same production database and external service accounts**. TEST is therefore **not data-isolated**. Safeguards against test emails, unintended writes, and customer exposure must be verified before handing out test URLs.

## 7. Short request summary

Please add **five Cloudflare DNS records** for `studio`, `admin`, `test`, `teststudio`, and `testadmin` under `askanna.online`, pointing to the **verified AskAnna origin**. These subdomains already exist on the hosting server but are not publicly resolvable. The existing `askanna.online` DNS and Cloudflare configuration should remain untouched. Once the records are live, the developer will complete SSL validation and test the separate LIVE/TEST application URLs.

## 8. Further questions

Please do check with ChatGPT, Claude or Gemini for adding DNS records, if above information is not sufficient and clear.

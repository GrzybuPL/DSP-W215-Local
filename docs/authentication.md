# HNAP authentication

This document records the working local authentication flow observed with a D-Link DSP-W215 B1 running firmware 2.02 and HNAP 0114.

Use the plug endpoint with a trailing slash: `http://<device-ip>/HNAP1/`.

## Challenge request

Send a SOAP `Login` request with `Action=request`, the configured username, and empty `LoginPassword` and `Captcha` values. The device responds with `LoginResult=OK` and the `Challenge`, `Cookie`, and `PublicKey` values.

Add the returned cookie to the HTTP session as `uid=<Cookie>` for the device host and `/` path. Keep the same session for the login and subsequent actions.

## Derive login values

All inputs below are UTF-8 strings. HMAC is HMAC-MD5 and the hexadecimal output is uppercase.

```text
PrivateKey = HMAC-MD5(key = PublicKey + device_password, data = Challenge)
LoginPassword = HMAC-MD5(key = PrivateKey, data = Challenge)
```

## Login request

Send another SOAP `Login` request with `Action=login`, the username, and `LoginPassword` set to the derived value.

For the HTTP headers, quote the full SOAP action URL, for example `"http://purenetworks.com/HNAP1/Login"`. The `HNAP_AUTH` header is computed as:

```text
timestamp = current Unix time in seconds
HNAP_AUTH = UPPERCASE_HEX(HMAC-MD5(key = PrivateKey,
                                  data = timestamp + quoted_SOAPAction))
            + " " + timestamp
```

A successful response contains `LoginResult=success`.

## Authenticated action

Retain the same `uid` cookie and create a fresh `HNAP_AUTH` for each action, using the current Unix timestamp in seconds and that action's quoted SOAP action URL. For example:

```text
"http://purenetworks.com/HNAP1/GetSocketSettings"
```

The observed socket state request uses `ModuleID=1` and returns the state in `OPStatus` (`true` or `false`).

## Security and privacy

The device password/PIN, `PrivateKey`, `LoginPassword`, challenge, cookie, and full unredacted device responses are secrets or may expose device-specific identifiers. Do not commit them. The device uses plain HTTP, so use this protocol only on a trusted local network or a trusted VPN.

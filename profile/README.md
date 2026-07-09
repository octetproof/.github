![Octet](chronograph.gif)

# Octet

**A device was here, at this time.** Octet is proof of location. Proof that a known device is where it claims to be, signed in hardware. Live for iOS and Android.

Ask whether a device is inside or outside a region. Get back a signed yes or no, verifiable offline. No coordinates leave the device.

## Why it exists

When you log in, send money, or hit buy, your phone attaches a location to the action. It reports what it was told, not what is true. Every signal it exposes can be faked: GPS, IP, the location services your apps rely on. $300 of hardware spoofs GPS. A five-dollar VPN moves your IP across the world. One free spoofing app has more than 50 million installs.

Every credential a system checks can be copied: a password, a document, a face. One thing cannot. Where your body is. You are here. You cannot also be there. The attacker wearing your identity is somewhere else.

Octet learns location from inertial motion, RF geometry, GPS, and signals most systems ignore, then signs it into a single proof. What leaves the device is a predicate: a hardware-signed yes or no against a policy. An attacker can steal everything except where the real user is.

## Repositories

| Repo | What it is | License |
| --- | --- | --- |
| [octet-sdk-ios](https://github.com/octetproof/octet-sdk-ios) | iOS SDK. Binary via Swift Package Manager. A license key unlocks it. | Proprietary |
| [octet-sdk-android](https://github.com/octetproof/octet-sdk-android) | Android SDK. Maven. A license key unlocks it. | Proprietary |
| [octet-verify](https://github.com/octetproof/octet-verify) | Open-source Rust verifier. Checks a proof offline, against the key the proof carries. No callback to Octet. | Apache-2.0 |
| [octet-attest-verify](https://github.com/octetproof/octet-attest-verify) | Offline App Attest and Play Integrity verification. | Apache-2.0 |
| [octet-policy](https://github.com/octetproof/octet-policy) | Open-source policy library. A policy answers a location question. Your code enforces the result. | Apache-2.0 |

You do not have to trust Octet. The proof is checked by octet-verify, open source, offline, with no callback. Octet's own proof storage holds bytes for 24 hours and is treated as untrusted by the verifier.

## Start here

- **Docs:** https://octetproof.com/docs/
- **For agents:** https://octetproof.com/llms.txt and https://octetproof.com/agents.md
- **OpenAPI 3.1:** https://octetproof.com/openapi.yaml
- **Free 90-day trial key:** https://sdk.octetproof.com/signup

Integrating takes about ten minutes: add the package, request the runtime permission, call `Octet.start`, then read a verdict.

```swift
import OctetSDK

let sdk = try await Octet.start(config: OctetConfig(licenseKey: "octet_live_…"))
let verdict = await sdk.loc.isWithin(region: .country(isoCode: "US"))
// verdict.result → YES / NO / INDETERMINATE
// verdict.proof  → hardware-signed, verifiable offline
```

## Contact

Developer and integration support: developer@octetproof.com

---

Understone, Inc. d/b/a Octet.

![Octet](chronograph.gif)

# Octet

**A device was here, at this time.** Octet is proof of location. Proof that a known device is where it claims to be, cryptographically signed. Live for iOS, Android and the browser.

Ask whether a device is inside a region and get back a verdict (YES, NO or INDETERMINATE) with a signed proof, verifiable offline. A policy can require, for example, that a payment is approved from a phone in the office. Your application decides what to do with the verdict. You can configure the proof to carry no coordinates.

## Why it exists

Every credential a system checks can be copied or synthesized: a password, a document, a face. Even when credentials work correctly, they work the same way wherever they are used, for the right person and the wrong person alike.

Location could tell them apart, but the location an application sees cannot be trusted. When a user logs in, sends money or hits buy, their phone attaches a location to the action. It reports what it was told, not what is true. Every signal it exposes can be faked: GPS, IP address, the location services apps rely on.

The Octet SDK makes location into a factor. It builds up a location on the device, learning from RF, inertial sensors and on-device data, including signals most systems ignore. It checks each signal for signs that it has been manipulated, and then it signs the result.

## Repositories

| Repo | What it is | License |
| --- | --- | --- |
| [octet-sdk-ios](https://github.com/octetproof/octet-sdk-ios) | iOS SDK. Swift Package Manager. Activates with App Attest, so there is no licence key to ship. | Proprietary |
| [octet-sdk-android](https://github.com/octetproof/octet-sdk-android) | Android SDK. Maven. Activates with hardware key attestation, so there is no licence key to ship. | Proprietary |
| [octet-sdk-react-native](https://github.com/octetproof/octet-sdk-react-native) | React Native package on npm. Binds the iOS and Android SDKs. | Proprietary |
| [octet-magistrate-ios](https://github.com/octetproof/octet-magistrate-ios) | Magistrate for iOS. Asks your location policy's question and returns the answer with a signed receipt. | Proprietary |
| [octet-magistrate-android](https://github.com/octetproof/octet-magistrate-android) | Magistrate for Android. The same, as an AAR on Maven. | Proprietary |
| [octet-browser](https://github.com/octetproof/octet-browser) | Octet Browser release downloads: the browser script and the edge service. A licence key unlocks it. | Proprietary |
| [octet-verify](https://github.com/octetproof/octet-verify) | Open-source Rust verifier. Checks a proof offline, against the key the proof carries. No callback to Octet. | Apache-2.0 |
| [octet-attest-verify](https://github.com/octetproof/octet-attest-verify) | Offline App Attest and Play Integrity verification. | Apache-2.0 |

You do not have to trust Octet. The proof is checked by octet-verify, open source, offline, with no callback. Storing proofs with Octet is opt-in, and the verifier does not rely on Octet's storage.

## Start here

- **Docs:** https://octetproof.com/docs/
- **Browser SDK:** https://octetproof.com/docs/browser/. Apply for access at https://browser.octetproof.com/signup
- **Policies:** write them in Magistrate, https://magistrate.octetproof.com/. Policies are signed bundles decided by the Octet policy engine.
- **For agents:** https://octetproof.com/llms.txt and https://octetproof.com/agents.md
- **OpenAPI 3.1:** https://octetproof.com/openapi.yaml
- **Register your app:** free for up to 1,000 unique devices a month, https://sdk.octetproof.com/signup

Integrating takes about ten minutes: add the package, request the runtime permission, call `Octet.start`, then read a verdict.

```swift
import OctetSDK

let sdk = try await Octet.start(config: OctetConfig())
let verdict = await sdk.loc.isWithin(region: .country(isoCode: "US"))
// verdict.result → YES / NO / INDETERMINATE
// verdict.proof  → signed on device, verifiable offline
```

## Contact

Developer and integration support: developer@octetproof.com

---

Understone, Inc. d/b/a Octet.

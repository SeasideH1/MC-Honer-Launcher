# Minecraft Services AppID application — MC Honer Launcher

Application form: https://aka.ms/mce-reviewappid

The text below describes `0.1.0-alpha.28`. Replace the two bracketed GUID placeholders with the application's actual Azure values before submission. The contact address must match the maintainer information available for cross-reference in Azure. This document is a prepared application, not a submission receipt or evidence of approval.

## Contact Information

qq1602770686@outlook.com

## 3. What type of request is this?

New AppID for Approval

This is a request to approve an application that is not currently allow-listed, following changes after a previous unsuccessful application. It is not a report about another application.

## 4. Application Name

MC Honer Launcher

Use this exact display name in the Azure application registration as well. MCHL is the abbreviation used in project documentation.

## 5. Application ID

[REPLACE WITH THE APPLICATION (CLIENT) ID — GUID]

## 6. Tenant ID

[REPLACE WITH THE DIRECTORY (TENANT) ID — GUID]

## 7. Associated website or domain

https://github.com/SeasideH1/MC-Honer-Launcher

## 8. Justification

I am the individual developer and product maintainer of MC Honer Launcher (MCHL), an independent desktop launcher for Minecraft: Java Edition. The application manages separate game instances, runtime settings and modpack updates. I request allow-list approval for the single AppID specified in this submission so that the application can authenticate consenting users through Microsoft's official authorization flow and verify their Java Edition entitlement and player profile through Minecraft Services.

Version 0.1.0-alpha.28 requires a verified Microsoft-linked Minecraft identity before creating a game process. Online verification checks the official entitlement and profile endpoints and binds the resulting UUID and profile name to the selected account. Independently created offline identities and third-party authentication identities cannot launch the game. A platform account, remote operator's access grant or OPL tunnel cannot replace this verification. OPL provides connectivity only and does not issue identities, grant game ownership or disable server authentication.

A previously verified account may use a locally protected verification record when disconnected. This record is bound to the same Minecraft access token and identity, expires no later than that token and at most 24 hours after verification, and is not renewed by offline use. Missing or expired verification blocks launch; an explicit rejection during online verification invalidates the record. The client does not substitute a tokenless identity. This bounded offline window cannot immediately detect a revocation occurring while disconnected and does not establish server admission.

MCHL does not redistribute vanilla Minecraft code, game binaries or resource assets. Modpack distribution is limited to custom content distributed under its applicable permissions. The project contains no commercial paid content, and testing access is not sold or tied to payments or donations. The public repository identifies the responsible developer, provides contact details and prominently states that the project is not an official Minecraft product and is not approved by or associated with Mojang or Microsoft.

## 9. Any other information that we should be aware of?

This resubmission follows a material change to the launch policy. Earlier development versions allowed independently created offline identities under a remote publisher's policy. Alpha.28 removes that launch capability: remote configuration and OPL connectivity cannot authorize an unverified identity. Older account records are retained for compatibility but are unusable for game launch. Historical documentation is explicitly identified as superseded.

An unsigned Windows x64 prerelease installer and SHA-256 checksum are available at:
https://github.com/SeasideH1/MC-Honer-Launcher/releases/tag/v0.1.0-alpha.28

The implementation, trust boundaries, offline-cache limitations and validation scope are documented at:
https://github.com/SeasideH1/MC-Honer-Launcher/blob/main/docs/AUTHENTICATION-ALPHA28.en.md

Validation includes 56 passing targeted tests, one explicitly skipped PostgreSQL test, a real child-process boundary test using a test executable, and packaged startup and bilingual UI smoke checks. Official authentication responses in these tests were controlled fixtures. These results do not establish successful live Microsoft authorization, Minecraft gameplay, cross-network OPL operation or authenticated server admission.

The public package currently has no approved Microsoft AppID configured. A fresh installation therefore permits interface inspection and instance management but cannot complete Microsoft sign-in or launch the game. It does not borrow another application's AppID or provide an alternative authentication route. I request approval for this application's own AppID before configuring it for distribution and completing live end-to-end validation. The application remains in development, and its development source repository is private.

Maintainer: SeasideH1, individual developer. Contact: qq1602770686@outlook.com.

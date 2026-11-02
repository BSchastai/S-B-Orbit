# S&B Orbit

A modern, lightweight launcher for Minecraft: Java Edition on Windows and Linux, built with Rust (Tauri v2) and React.

S&B Orbit (also written "SB Orbit") is a personal, non-commercial launcher and mod management client. It needs access to Minecraft Services only to sign in legitimate game owners, verify ownership and start the game they own.

## Status

In development. The source code is not public yet. Installers for Windows and Linux will be published on this repository's [Releases](https://github.com/BSchastai/S-B-Orbit/releases) page.

## Security and API usage

1. **Sign-in:** Microsoft OAuth 2.0 device code flow. Passwords and 2FA are entered only on Microsoft's website; the launcher never sees, reads or logs them.
2. **Token storage:** after the Xbox Live → XSTS → Minecraft Services exchange, the Microsoft refresh token is stored only in the operating system's credential vault (Windows Credential Manager / Secret Service). Tokens are never written to plain-text files, JSON or the app database. Minecraft access tokens are kept in memory only.
3. **No backend:** there is no intermediary server. All requests go directly from the user's computer to login.microsoftonline.com, user.auth.xboxlive.com, xsts.auth.xboxlive.com and api.minecraftservices.com.
4. **Official downloads:** game files, libraries, assets and Java runtimes are downloaded unmodified from Mojang's official servers (piston-meta.mojang.com, libraries.minecraft.net, resources.download.minecraft.net) and verified by SHA-1.
5. **API scope:** only /authentication/login_with_xbox, /minecraft/profile and /entitlements/mcstore are used, to get the player's UUID, name and skin and to start the local game process.
6. **Offline play:** only available after a Microsoft account that owns the game has signed in.

## Disclaimer

NOT AN OFFICIAL MINECRAFT PRODUCT. NOT APPROVED BY OR ASSOCIATED WITH MOJANG OR MICROSOFT.

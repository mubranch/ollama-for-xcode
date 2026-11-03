# Privacy Policy

**Ollama for Xcode** — last updated: November 3, 2026

Ollama for Xcode does not collect, sell, or share personal data, and it sends nothing to the developer. We run no servers for this app, and it contains no analytics, advertising, tracking, or crash-reporting code.

## What the app does with your data

The app connects Xcode's coding assistant to an Ollama server you choose. Everything happens on your Mac or on the server you configure.

- **Prompts and project content.** When you chat in Xcode, the agent sends your prompts and any project content the model asks to read (through Xcode's own tools) to the Ollama server address set in the app. By default that is `http://localhost:11434` on your own Mac. If you point the app at a remote server, your data is sent to that server and is governed by whoever operates it.
- **Conversation history.** Conversations are saved only on your Mac, in the app's container, so Xcode can resume them. You can delete them at any time from the app (Sessions → Delete All).
- **Settings.** Your configuration (server address, model names, context size) is stored in the app's local preferences.
- **Folder access.** The app asks you to grant access to Xcode's agent list folder (`~/Library/Developer/Xcode/CodingAssistant/ACP`). The permission is used only to register the agent with Xcode.
- **Diagnostics.** The app can build a diagnostics report. It is copied to your clipboard only when you click Copy Report, and it is never sent anywhere automatically.

## Third parties

The app talks only to the Ollama server you configure and to Xcode on your Mac. If you use a remote or cloud-hosted Ollama server, review that provider's privacy policy.

## Children

The app is a developer tool and is not directed to children.

## Changes

If this policy changes, the updated version will be posted at this address with a new date.

## Contact

Questions: **mustafa.branch@gmail.com**

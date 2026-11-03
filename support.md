# Ollama for Xcode — Support

Contact: **mustafa.branch@gmail.com**. Include your macOS version, Xcode version, and the diagnostics report (see below).

## Requirements

- macOS 14 or later and an Xcode version with the Coding Assistant (custom agent) feature.
- [Ollama](https://ollama.com) running locally, or reachable at an address you set.
- A model that supports tool calling (for example `qwen2.5-coder` or `llama3.1`). Models without tool support can chat but cannot read or edit your project.

## Getting started

1. Open Ollama for Xcode and keep it in your Applications folder.
2. Start Ollama and pick a model in the app.
3. Click **Allow Access…** and choose the `ACP` folder (`~/Library/Developer/Xcode/CodingAssistant/ACP`). If it does not exist, choose `Xcode` in `~/Library/Developer`.
4. Click **Register with Xcode**, then quit Xcode (⌘Q) and reopen it.
5. In Xcode, open the Coding Assistant, start a new conversation, and choose your model.
6. The first time, Xcode asks "Allow OllamaForXcode to access Xcode?". Click **Allow**.

No Ollama? Turn on **Demo mode** in the app to explore it with sample models. Chatting in Xcode still needs a running Ollama server.

## Troubleshooting

| Problem | Fix |
| --- | --- |
| "Could not reach Ollama" | Start Ollama (menu bar app or `ollama serve`) and check the server address. |
| Agent missing in Xcode | Click **Update Registration**, then quit and reopen Xcode. |
| Conversation hangs on start | Xcode is waiting on the "Allow … to access Xcode?" prompt. It asks again for each new agent process. Click **Allow**. |
| Model replies but never edits files | The model lacks tool calling. Choose one that supports it. |
| Slow or cut-off answers | Lower the context length or use a smaller model. |

## Diagnostics

In the app, open **Diagnostics** and click **Copy Report** to attach details to your message. The report contains settings and check results, not your conversations.

## Privacy

See the [Privacy Policy](privacy.md).

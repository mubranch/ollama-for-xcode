# Ollama for Xcode Agent (free download)

A free, standalone version of the agent that the Mac App Store app bundles. It lets Xcode's Coding Assistant use models running in [Ollama](https://ollama.com).

The Mac App Store app adds a point-and-click setup, diagnostics and model management. This download is the agent alone, configured by hand.

## Requirements

- macOS 15.6 or later and Xcode 26.3 or later (Coding Assistant with custom agents)
- Ollama running locally or on your network
- A model that supports tool calling, for example `ollama pull qwen2.5-coder:14b`

## Install

1. Download `OllamaForXcodeAgent.zip` from the [latest release](https://github.com/mubranch/ollama-for-xcode/releases/latest) and unzip it.
2. Move the agent somewhere permanent and make it executable:

   ```sh
   mkdir -p ~/.local/bin
   mv OllamaForXcodeAgent ~/.local/bin/
   chmod +x ~/.local/bin/OllamaForXcodeAgent
   ```

3. Create an agent entry for Xcode. Save the following as
   `~/Library/Developer/Xcode/CodingAssistant/ACP/OllamaForXcode.plist`
   (create the folder if it doesn't exist), replacing `YOUR_USER` and the model name:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
       <key>agent</key>
       <string>/Users/YOUR_USER/.local/bin/OllamaForXcodeAgent</string>
       <key>arguments</key>
       <array>
           <string>--model</string>
           <string>qwen2.5-coder:14b</string>
           <string>--ollama-url</string>
           <string>http://localhost:11434</string>
           <string>--context-length</string>
           <string>32768</string>
       </array>
       <key>environment</key>
       <dict/>
       <key>name</key>
       <string>Ollama – qwen2.5-coder:14b</string>
   </dict>
   </plist>
   ```

4. Quit Xcode (⌘Q) and open it again, then choose the agent in Xcode's Coding Assistant settings.
5. The first time, Xcode asks whether to let the agent access Xcode. Choose **Allow**.

Add one plist per model to offer several.

## Options

| Option | Description |
|---|---|
| `--model <name>` | Ollama model to use. Required. |
| `--ollama-url <url>` | Ollama address. Default `http://localhost:11434`. |
| `--context-length <n>` | Context length in tokens. |
| `--all-tools` | Give the model all Xcode tools instead of the core set. |
| `--session-directory <path>` | Where conversations are saved. Default `~/Library/Application Support/OllamaForXcode/Sessions`. |

## Troubleshooting

- Test the agent starts: `~/.local/bin/OllamaForXcodeAgent --model qwen2.5-coder:14b` (it waits for Xcode on standard input; press ⌃C to stop).
- Watch the logs while you chat in Xcode:
  `log stream --level debug --predicate 'subsystem == "com.mubranch.OllamaForXcodeAgent"'`
- Verify the download: `codesign -dv --verbose=2 OllamaForXcodeAgent` should show Developer ID Application: Mustafa Branch (48Q6PX46H2).

## Privacy

The agent sends your prompts and the project files you ask it to read only to the Ollama server you configure. It collects no data. See the [Privacy Policy](privacy.md).

## License

Free to use for personal and commercial work under the [license](LICENSE.md). Support: [support.md](support.md).

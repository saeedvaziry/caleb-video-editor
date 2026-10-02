# Storyboard

https://github.com/user-attachments/assets/39517db2-fff0-48b7-9274-f2108ecaec5d

A local, prompt-driven motion-design editor. Every scene is a small piece of code; you change it by chatting with Claude Code or Codex next to a live preview, down to the millisecond. Finished videos export to MP4.

Inspired by [Caleb Porzio's tweet](https://x.com/calebporzio/status/2104945478055989489) about the editor he vibe-coded for his video.

![The Storyboard editor: a live preview, the scene chat, and the filmstrip](docs/screenshot.png)

- **Chat per scene, or about the whole video**, next to a live preview.
- **Music that drives the edit**: beats, bars and phrases are detected, and cuts snap to them.
- **Sound effects** placed on the same timing as the animation.
- **Optional**: Your agent composes the soundtrack and generates realistic sound effects, on your own machine.

## Get started

You need macOS or Linux and [Node.js](https://nodejs.org) 22.12 or newer.

```bash
git clone https://github.com/saeedvaziry/caleb-video-editor.git
cd caleb-video-editor
./storyboard setup
./storyboard start
```

![./storyboard setup in a terminal: it checks the basics, asks about music and sound-effect generation, installs everything with progress bars, then starts Storyboard](docs/setup.gif)

Setup walks you through the rest (ffmpeg, your Claude Code or Codex login, and whether you want music and sound-effect generation) and installs everything inside this folder. Run it again any time to change your choices. It installs packages with `npm ci --ignore-scripts`, so no package's install script ever runs: don't use `npm install` here.

### Using Codex

Install a current [Codex CLI](https://developers.openai.com/codex/cli) (0.159.0 or newer recommended) and run `codex login`. Choose **Codex** in setup or in the chat's agent selector; Claude Code is not required. The model selector reads the models and reasoning levels in Codex's local catalog, with **Codex default** available even before the catalog is populated.

For non-interactive setup: `./storyboard setup --yes --provider=codex`. To override the default at startup: `STORYBOARD_PROVIDER=codex ./storyboard start`. Both agents remain available in the editor when installed.

### Custom address and port

`./storyboard setup --yes --host=0.0.0.0 --port=5299` saves the bind address and port (`--ip` also works). Then run `./storyboard start`, or `./storyboard restart app` if it is already running. Open `http://<server-LAN-IP>:5299` from another device. The default remains localhost only.

**Network access has no login:** anyone who can reach the port can edit projects and use your agents. Use a trusted network/firewall, never the public internet. See [configuration](docs/configuration.md#bind-address-and-port).

## Commands

| | |
| --- | --- |
| `./storyboard setup` | Install, or change what's installed |
| `./storyboard start` | Start Storyboard in the background |
| `./storyboard stop` | Stop it |
| `./storyboard status` | See what's running |
| `./storyboard logs` | Show the log |
| `./storyboard doctor` | Check that everything is in place |

## More

- [Using Storyboard](docs/using-storyboard.md): the editor, sound effects, and the tools from your terminal
- [Music and sound effects](docs/music-and-sound.md): the optional engines
- [Configuration](docs/configuration.md) · [Troubleshooting](docs/troubleshooting.md)
- [How it works](docs/how-it-works.md) · [Developing Storyboard](docs/development.md)

## License

[MIT](LICENSE) © 2026 Saeed Vaziry. The optional music engine, ACE-Step 1.5, has its own MIT license; the optional sound model, Stable Audio Open 1.0, is downloaded from Hugging Face under the Stability AI Community License.

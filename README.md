# Christmas Eve 🎄

A Christmas mode for [Claude Code](https://claude.com/claude-code): falling snow and fairy lights above the prompt, a festive spinner, a countdown to Christmas Eve, and a snowy backdrop in the desktop app.

```
──●───●───●───●───●─── 31 days till Christmas Eve ●───●───●───●───●───●─
     ·*    ·      *              *           ·           ·         ·
 ·      · ·  *       ·      * *            **     ·             ·   *
   ·     *                         ·     ·      ·  ·  *  ·
> _
```

## What you get

**In the terminal**

- **Snow band.** A string of slowly twinkling fairy lights over falling snow, above the prompt. The snow falls gently while the session is idle and turns into a wind-blown flurry while Claude works.
- **Countdown.** From 1 November the lights carry the days left until Christmas Eve, then "It's Christmas Eve" on the 24th and "Merry Christmas" on the 25th and 26th. The rest of the year the lights hang alone.
- **Festive spinner.** "Baking Lebkuchen… ❄", "Feeding the reindeer… ❄", "Untangling the lights… ❄" while Claude works, and a matching line when a turn ends ("Jingled for 12s").
- **Color theme.** A dark terminal theme in pine green, cranberry and gold. Pick **Christmas Eve** in `/theme`.

**In the desktop app's Code tab** (local sessions)

- A snow scene behind the chat, with pines, a lit cabin, chimney smoke and fairy lights, and matching colors in light and dark mode.

## Install

The repository holds the packaged plugin, `christmas-eve.plugin`, which is a zip archive.

1. Download `christmas-eve.plugin` and unpack it into a folder of its own:

   ```sh
   unzip christmas-eve.plugin -d ~/christmas-eve
   ```

2. Start Claude Code with that folder as a plugin:

   ```sh
   claude --plugin-dir ~/christmas-eve
   ```

To load it in every session, including the ones the desktop app starts, name the folder in the `env` block of `~/.claude/settings.json` instead (an absolute path or one starting with `~`):

```json
{
  "env": {
    "CLAUDE_CODE_PLUGIN_DIRS": "~/christmas-eve"
  }
}
```

The plugin is a hooks module, a kind of plugin that is in early access and whose API moves between releases. This version was built and tested against Claude Code 2.1.330.

## Commands

| Command | What it does |
| --- | --- |
| `/christmas` or `/christmas on` | Turns Christmas mode on. |
| `/christmas off` | Turns it off. It stays off in later sessions until you turn it on again. |
| `/christmas quiet` | Hides or shows the snow band, keeping the spinner and the colors. |

## Good to know

- Everything in the terminal is drawn by the terminal itself, so it works over SSH and on remote dev servers.
- The snow band stops repainting while it is collapsed (ctrl+x ctrl+a), gets shorter on a short terminal, and leaves the countdown out on a narrow one.
- The countdown follows the date of the machine Claude Code runs on.
- The lights change slowly and never flash.
- The desktop backdrop does not show in WSL sessions, cloud sessions or through Remote Control. On Windows it needs Transparency effects turned on.

## What is in the package

| Path | What it is |
| --- | --- |
| `.claude-plugin/plugin.json` | The plugin's manifest. |
| `hooks/register.tsx` | The hooks module: the command, the band, the spinner, the backdrop. |
| `hooks/snow.ts` | The snow simulation, the lights, the countdown and the festive words. |
| `hooks/scene.js` | The desktop backdrop, an animated vector scene. |
| `hooks/make-colors.js` | Builds the desktop color theme from a few colors and checks its contrast. |
| `themes/christmas-eve.json` | The terminal color theme. |
| `tests/` | Tests, run with `claude plugin test <folder>`. |

## Changes

**0.3.0**

- The snow turns into a flurry while Claude works.
- A countdown to Christmas Eve in the lights.
- The snow band rests while collapsed and fits short terminals.
- A mistyped `/christmas` argument shows the usage instead of turning the mode on.
- More festive spinner words.

**0.2.1**

- First published version.

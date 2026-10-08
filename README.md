# slopping-verbs

Mess with the verbs in the Claude Code thinking spinner. Add "Slopping...", kick out "Pondering...".

It edits the `spinnerVerbs` setting in `~/.claude/settings.json` and leaves everything else in that file alone. No dependencies, just Python 3.10+.

## Install

```bash
ln -s "$PWD/verb" ~/.local/bin/verb
```

## Use

```bash
verb --add Slopping "Gaslighting the compiler"
verb --remove Pondering Clauding
verb --list          # your verbs and the stock ones you removed
verb --all           # everything currently in rotation
verb --starter       # load a pack of funny verbs
verb --only-mine     # drop every stock verb
verb --roll          # preview a random one
verb --reset         # back to stock Claude
```

Short flags work too: `-a`, `-r`, `-l`.

New sessions pick up the changes. Set `CLAUDE_CONFIG_DIR` if your config lives somewhere other than `~/.claude`.

## How removing stock verbs works

Claude Code only lets you `append` to the stock list or `replace` it. So the first time you remove a stock verb, `verb` switches to `replace` mode and writes out the full stock list minus the ones you removed, plus your own. The stock list is baked into the script from Claude Code 2.1.289, so verbs Anthropic adds later won't show up until you `--reset`.

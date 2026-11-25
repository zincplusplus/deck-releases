# deck-releases

`deck-wired`: the cable half of the deck, for Macs where only the cable is allowed. It never touches the network.

## Install or update

Run it from the folder your repos live in: that folder is where New sessions open. It runs inside a cmux pane and inherits cmux's Accessibility and Screen Recording, so nothing to sign or grant.

```bash
mkdir -p ~/.local/bin && curl -sL https://github.com/zincplusplus/deck-releases/releases/latest/download/deck-wired -o ~/.local/bin/deck-wired.new && chmod +x ~/.local/bin/deck-wired.new && mv ~/.local/bin/deck-wired.new ~/.local/bin/deck-wired && cmux workspace create --name Deck --cwd "$PWD" --command 'while :; do ~/.local/bin/deck-wired; sleep 2; done'
```

To update: run the same line without the final `cmux workspace create` part. The running tool sees the new build on disk, quits, and the pane's loop starts it.

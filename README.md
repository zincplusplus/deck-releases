# deck-releases

`deck-wired`: the cable half of the deck, for Macs where only the cable is allowed. It never touches the network.

## Install or update

It runs inside a cmux pane and inherits cmux's Accessibility and Screen Recording, so nothing to sign or grant. The argument is the projects folder that New sessions open under.

```bash
curl -sL https://github.com/zincplusplus/deck-releases/releases/latest/download/deck-wired -o ~/.local/bin/deck-wired && chmod +x ~/.local/bin/deck-wired && cmux workspace create --name Deck --command 'while :; do ~/.local/bin/deck-wired ~/Atlassian; sleep 2; done'
```

To update: run the first half again (the `curl` and `chmod`), then press ctrl-c in the Deck pane. The loop restarts the new build.

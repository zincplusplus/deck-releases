# deck-releases

`deck-wired`: the cable half of the deck, for Macs where only the cable is allowed. It never touches the network.

## Install or update

Paste in a cmux pane, from the folder your repos live in: that folder is where New sessions open, and the pane keeps running the tool. Inside cmux it inherits Accessibility and Screen Recording, so nothing to sign or grant.

```bash
mkdir -p ~/.local/bin && curl -sL https://github.com/zincplusplus/deck-releases/releases/latest/download/deck-wired -o ~/.local/bin/deck-wired.new && chmod +x ~/.local/bin/deck-wired.new && mv ~/.local/bin/deck-wired.new ~/.local/bin/deck-wired && while :; do ~/.local/bin/deck-wired; sleep 2; done
```

Since 2.37 the tool transcribes speech itself (Parakeet TDT v3). The first launch downloads the 461 MB model from huggingface.co into ~/Library/Application Support/FluidAudio; talk says "Loading speech model" until the pane logs "speech: Parakeet v3 ready". Behind a proxy, set `https_proxy` in the pane first.

To update, from any other pane: the same line without the final `while` loop. The running tool sees the new build on disk, quits, and the loop starts it.

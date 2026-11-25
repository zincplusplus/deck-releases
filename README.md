# deck-releases

Two tools for a Mac whose network is not ours to use. Neither touches a network interface.

- `deck-ble`: the deck over Bluetooth. The iPad advertises, the Mac connects, and macOS pairs the two once with its own dialog. Range is the same room.
- `deck-wired`: the deck over the USB cable.

## Bluetooth

Paste in a cmux pane, from the folder your repos live in: that folder is where New sessions open, and the pane keeps running the tool. Inside cmux it inherits Accessibility and Screen Recording, so nothing to sign or grant.

```bash
mkdir -p ~/.local/bin && curl -sL https://github.com/zincplusplus/deck-releases/releases/latest/download/deck-ble -o ~/.local/bin/deck-ble.new && chmod +x ~/.local/bin/deck-ble.new && mv ~/.local/bin/deck-ble.new ~/.local/bin/deck-ble && while :; do ~/.local/bin/deck-ble; sleep 2; done
```

First run: macOS asks for Bluetooth for cmux, allow it. Open Deck on the iPad next to the Mac; both show a 6-digit code, confirm on both. The pane logs "iPad over Bluetooth" when linked. To revoke, forget the iPad in System Settings > Bluetooth.

Talk over Bluetooth dictates on the iPad and sends the words, so this tool loads no speech model.

## Cable

`deck-wired` never leaves the cable.

Same pane, same folder:

```bash
mkdir -p ~/.local/bin && curl -sL https://github.com/zincplusplus/deck-releases/releases/latest/download/deck-wired -o ~/.local/bin/deck-wired.new && chmod +x ~/.local/bin/deck-wired.new && mv ~/.local/bin/deck-wired.new ~/.local/bin/deck-wired && while :; do ~/.local/bin/deck-wired; sleep 2; done
```

Since 2.37 the tool transcribes speech itself (Parakeet TDT v3). The first launch downloads the 461 MB model from huggingface.co into ~/Library/Application Support/FluidAudio; talk says "Loading speech model" until the pane logs "speech: Parakeet v3 ready". Behind a proxy, set `https_proxy` in the pane first.

To update either tool, from any other pane: the same line without the final `while` loop. The running tool sees the new build on disk, quits, and the loop starts it.

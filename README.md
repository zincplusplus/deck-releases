# deck-releases

Deck Wired for Mac: notarized builds. The cable half of the deck, for Macs where only the cable is allowed. It never touches the network.

## Install or update

Quits Deck Wired, downloads the latest release into ~/Applications and opens it. It adds itself as a login item. Then grant it Accessibility and Screen Recording in System Settings, and pick the projects folder from its menu bar icon.

```bash
pkill -x "Deck Wired"; cd /tmp && rm -f Deck-Wired.zip && curl -sLO https://github.com/zincplusplus/deck-releases/releases/latest/download/Deck-Wired.zip && mkdir -p ~/Applications && rm -rf ~/Applications/"Deck Wired.app" && ditto -x -k Deck-Wired.zip ~/Applications && open ~/Applications/"Deck Wired.app"
```

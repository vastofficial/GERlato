# GERlato
A copy of Gelato for my German library on Jellyfin. 

*Jellyfin Stremio Integration Plugin (repackaged)*

Gerlato is a repackaged distribution of [**Gelato**](https://github.com/lostb1t/Gelato) by [lostb1t](https://github.com/lostb1t), a plugin that brings the Stremio addon ecosystem directly into Jellyfin. It replaces Jellyfin's default search with Stremio-powered results and can import entire catalogs into your library through scheduled tasks, so streamed items behave like native library items.

This repository redistributes the official upstream release binaries under a separate plugin repository. **No code changes were made.** All development credit belongs to the original author. If you find this useful, please [star the upstream repo](https://github.com/lostb1t/Gelato) and consider [supporting lostb1t on Ko-fi](https://ko-fi.com/lostb1t).

## Features

- **Unified Search** – Jellyfin search pulls results from Stremio addons
- **Catalogs** – Import items from Stremio catalogs via scheduled tasks
- **Realtime Streaming** – Streams are resolved on demand and play instantly
- **Database Integration** – Stremio items appear like native Jellyfin items
- **Proxy Mode** – Streams are proxied through Jellyfin, so debrid providers see a single IP
- **Per-User Settings** – Each user can have their own manifest (useful for age-restricted accounts)

## Requirements

- Jellyfin **10.11.x** (targetAbi `10.11.6.0`)
- An [AIOStreams](https://github.com/Viren070/AIOStreams) manifest (self-hosted or public instance). Only AIOStreams is supported.

## Installation

1. In Jellyfin, go to **Dashboard → Plugins → Repositories → Add** and enter:

   ```
   https://raw.githubusercontent.com/YOURUSER/Gerlato/main/repository.json
   ```

2. Go to **Catalog → General → Gerlato → Install**, then restart Jellyfin.
3. Configure the plugin with your AIOStreams manifest URL. At minimum, enable the **TMDB addon** for search plus one stream-providing addon.
4. Add the configured base paths to a Jellyfin library and start a library scan.
5. For shows, enable the missing season/episode fetcher and place it at the top of the metadata downloaders.

For detailed setup, follow the [upstream starter guide](https://github.com/lostb1t/Gelato/discussions/40). All upstream documentation applies to this build unchanged.

## Notes

- **Same plugin GUID as upstream Gelato.** Jellyfin treats Gerlato and Gelato as the same plugin. Do not add both plugin repositories at once; updates will come from whichever repository advertises the higher version.
- This repo tracks upstream releases manually and may lag behind. For the latest version, use the [official repository](https://github.com/lostb1t/Gelato).
- Restart the Jellyfin server after editing your AIOStreams manifest/config.
- If something breaks or you want a clean start, run the purge task under Scheduled Tasks.

## License

This project is distributed under the **GNU General Public License v3.0**, the same license as the upstream project. See [LICENSE](LICENSE).

- Original source code: https://github.com/lostb1t/Gelato
- Original author: [lostb1t](https://github.com/lostb1t)
- Changes in this distribution: renamed plugin manifest entry and main assembly file from `Gelato` to `Gerlato`; no source code modifications.

## Disclaimer

This plugin is a tool for integrating Stremio addons with Jellyfin. You are responsible for the addons you configure and the content you access through them. Use only with content you have the legal right to stream.

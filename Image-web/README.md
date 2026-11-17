# Image Web

Drop images into a 3D space, connect them with lines, and write a small essay inside every connection. Everything runs in your browser: no account, no server, nothing uploaded.

## Features
- Unlimited images, audio and video (drag in, paste, or use *Insert media*) plus written notes (*New note*), floating in a 3D space you can orbit, pan, and zoom
- Connect any two items; each connection holds a title, an essay, and a color
- Click an image to center the view on it and write an essay about that image (a small dot marks images that have one)
- **Fit view** frames the whole web and slowly spins it for a showcase view until you touch it (paused while any menu is open)
- **Arrows:** set any connection to one-way or mutual; animated arrows flow along the line in the direction you choose
- **Family-tree links:** in Connect mode a connection's glowing dot can itself be connected to another item (for example, two parents joined by a dot, with an arrow from that dot to a child)
- **Resize** any image, video, audio card, or note with the Size slider in its panel, or Alt + scroll while hovering it
- Ambiance presets, adjustable stars and drift
- Soft synthesized sound effects, plus your own looping background music
- **Export / Import** your whole web as one `.json` backup file

## Use it
Open `index.html` in a modern browser, or host the folder on any static host.

### Offline
The page loads three.js (r128) from a CDN. For fully offline use, download
<https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js> and save it as `three.min.js` next to `index.html`. The page falls back to that file automatically.

### Publish on GitHub Pages
1. Create a new public repository and upload `index.html`, `README.md`, and `LICENSE` (add `three.min.js` if you want the offline copy).
2. Go to **Settings > Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
3. After a minute your site is live at `https://YOUR-USERNAME.github.io/REPO-NAME/`.

## Your data
Your web is stored in your browser (IndexedDB) for the site you opened it on. It stays on your device, but clearing site data erases it, so export a backup now and then. Backups include images, connections, essays, colors, layout, and ambiance. Music is not included. Audio and video files over 40 MB are skipped, and backups embed all media, so they can get large.

Importing asks whether to replace your current web or add the backup alongside it.

## Credits
Built with [three.js](https://threejs.org) (MIT).

## License
MIT. See `LICENSE`.

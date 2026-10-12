# The Room — Puzzle Prototype

A beginner-friendly HTML/CSS/JavaScript prototype with local portrait images in `images/`. No framework or build step is required.

## Run the live preview locally

From this folder, start a simple local server:

```sh
python3 -m http.server 8000
```

Open <http://127.0.0.1:8000/> in your browser. Save edits to `index.html` or files under `images/`, then refresh the page to see them. Use the left/right arrow keys or on-screen arrows to turn between the five walls. The password is `Mellon`, accepted in any letter case.

## Before sharing with your friend

Open `index.html` in a text editor and search near the bottom for:

```js
const ACCEPTED_PASSWORD = "Mellon";
const WALL4_BANNER = "Use ⬛ to find ⚫";
const WALL4_MESSAGE = "STATEN ISLAND\nSPEAK FRIEND AND ENTER";
```

The photo and frame pairs on Walls 1 and 2, and the Wall 3 displays, shuffle when the page opens. The Wall 4 message is encoded with a random Caesar shift from 1 to 25 on each page load. Wall 5 stays locked and out of the arrow-key loop until `Mellon` is entered in any letter case; refreshing starts a new locked session.

**Important:** because this first version runs entirely in the browser, the accepted password is visible in the source code. This is fine for a casual puzzle test, but it is not secure against someone inspecting the page.

## Wall portraits

Wall 1 and Wall 2 use individual local portrait images in `images/`. Wall 1 frames match each photo's natural proportions; each photo stays paired with its frame as the pairs rearrange on each page load. Caesar is in the only square frame. Wall 2 has eleven Morgan Freeman portraits, with Red in its only circular frame and the other ten in oval frames. The Jolie photo is cropped to Morgan Freeman only. The photographs have no visible captions.

To change a portrait, replace the relevant image file or adjust the photo indices in `renderWall1` and `renderWall2` in `index.html`. Wall 3 and Wall 4 are separate from these galleries.

## Publish using GitHub Pages

1. Sign in to GitHub and create a new **public repository**, e.g. `puzzle-room`.
2. Upload `index.html` to the repository root (you can also include this README and your `images` folder).
3. Open the repository's **Settings → Pages**.
4. Under the build/deployment settings, choose **Deploy from a branch**.
5. Select the `main` branch and `/ (root)`, then save.
6. Wait for GitHub Pages to publish the site. The Pages screen will show the URL; it usually looks like `https://YOUR-USERNAME.github.io/puzzle-room/`.
7. Open that URL yourself and test the five walls and password before sending it to your friend.

## Current prototype details

- Four walls are available initially; Wall 5 stays locked and out of the arrow-key loop until the password is entered. Refreshing relocks it.
- Wall 1: eleven monkey portraits in correctly proportioned frames; photo/frame pairs rearrange on each page load. Caesar has the only square frame.
- Wall 2: eleven uploaded Morgan Freeman portraits, shuffled on each page load, with ten oval frames and exactly one circular frame for Red.
- Wall 3: uploaded clue photos and the blank display shuffle on each page load; the four colored frames swap colors, while the blank stays red. There are no captions. The Brooklyn Beckham photo is cropped to keep the plate out of view.
- Wall 4: banner “Use ⬛ to find ⚫” and “STATEN ISLAND / SPEAK FRIEND AND ENTER” encoded with a new nonzero Caesar shift on each page load.
- Password `Mellon` (case-insensitive) opens Wall 5, which says “The Puzzlemaster will see you now.”

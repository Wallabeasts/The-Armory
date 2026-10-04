# The Armory

Two small web apps for the Etsy shop [Theworkshp](https://www.etsy.com/shop/Theworkshp): a customer app and a private developer app for the shop owner. Version: alpha 0.2.

| File | What it is |
| --- | --- |
| `index.html` | Customer app: helmets, custom print estimates and print requests |
| `developer.html` | Developer app: order bench, profit calculator, listing writer, Etsy import, printer link |
| `photo-*.jpg` | Optional helmet photos for the customer app (see below) |
| `icon-*.png`, `*.webmanifest` | Home-screen icon and install settings |

There is no build step and no server. Each app is a single HTML file.

## Put it online with GitHub Pages

1. Create a new repository on GitHub and upload every file in this folder. There are no subfolders, so this works from a phone too.
2. Open the repository's **Settings**, then **Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick the `main` branch and the `/ (root)` folder, and save.
4. After a minute the customer app is live at `https://YOUR-USERNAME.github.io/REPO-NAME/` and the developer app at `.../developer.html`.

On a phone, open either address and choose **Add to Home Screen** to install it like an app.

## What it does and does not do

- Orders, saved helmets, requests and settings are stored in the browser on each person's own device. Nothing is sent to a server, and the two apps do not share data.
- Customers send print requests through Etsy messages. The owner pastes a request into the developer app to turn it into an order.
- Payment happens on Etsy.
- The developer app opens the printer's own control page. It cannot send files to the printer itself.
- The listing writer uses a fill-in template here. The Claude-written version only works in the copy published on claude.ai.

## Helmet photos

Upload one photo per helmet next to the other files, using these exact names. A helmet with no photo shows as a text card.

| Helmet | File name |
| --- | --- |
| Mark 39 helmet | `photo-mark39.jpg` |
| Symbiote Spiderman helmet | `photo-symbiote.jpg` |
| Wearable decorated Mandalorian helmet | `photo-mando-deco.jpg` |
| Mandalorian helmet, unfinished | `photo-mando-raw.jpg` |
| Mandalorian helmet, finished | `photo-mando-fin.jpg` |

## Settings to change

**Print prices and printer size.** In `index.html`, find the block that starts with `var SHOP={`. The rates, materials, colours and minimum order are all there. The numbers that ship with this version are placeholders, so set real ones before quoting customers. The printer size is set for an Elegoo Neptune 4 Plus (320 x 320 x 385 mm).

**Helmets.** The helmet list appears in both files: `var HELMETS=[` in `index.html` and `var CATALOG=[` in `developer.html`.

**Developer passcode.** The developer app opens to a lock screen. To change the passcode:

1. Open `developer.html` in a browser and open the browser console.
2. Run `__sha256("armory:" + "your-new-passcode")` using lowercase letters.
3. Copy the result into `var PASS_HASH="..."` in `developer.html`.

The lock keeps ordinary visitors out of the owner tools, but this is a public web page and its code can be read by anyone, so treat it as a deterrent and not as real security. The owner's orders are never in the code; they live only in the browser on the owner's device.

## Testing

Use **Report a problem** (Help tab in the customer app, Shop tab in the developer app) to copy a report with the device details.

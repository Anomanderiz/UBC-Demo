# UBC giving form: mobile prototype

A single self-contained `index.html`. No build step, no dependencies.

## Deploy to Vercel

Fastest route, from this folder:

```
npx vercel
```

Accept the defaults; Vercel treats a folder containing `index.html` as a static
site with no configuration. `npx vercel --prod` promotes it to a stable URL.

Alternatively, drag the folder onto the Vercel dashboard's new-project screen,
or push it to a GitHub repository and import that.

To test locally on your phone over the same wifi:

```
python3 -m http.server 8080
```

then open `http://<your-laptop-ip>:8080` on the handset.

## Swapping in the real typeface

Two CSS custom properties at the top of `index.html` control all type:

```css
--font-display: ...;
--font-body:    ...;
```

Whitney is served from `cloud.typography.com` and is domain-locked to approved
`*.ubc.ca` hosts, so it cannot render on a Vercel URL. On a UBC host, add the
stylesheet link from the CLF instructions and set both properties to
`'Whitney SSm A','Whitney SSm B',Arial`. The serif currently in the live giving
pages is neither Whitney nor Guardian Egyptian; if Digital Communications can
name it, drop it into these two lines.

## Colours

`--ubc-blue: #002145` is the official brand blue from brand.ubc.ca. The gold on
the give button, the pill grey and the page grey were eyedropped from the
screenshots of the current form and should be confirmed against the real
stylesheet before anyone treats them as brand-accurate.

## Structure

Five steps: cause, amount, about you, receipt address, payment. The wallet
button on the amount step bypasses steps three to five entirely. Both wallets
are always shown for demo purposes; a live build would show only the one the
device supports. Nothing is submitted anywhere; the
payment fields are ordinary inputs, not a gateway iframe, so do not type a real
card number into it.

The "Why this design" link at the bottom opens the rationale sheet, which is
the part worth showing across a table.

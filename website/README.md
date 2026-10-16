# Thus Spoke Zakura website

Static public site for Thus Spoke Zakura. Host this directory as the site root; it has no build step.
The application dashboard remains in `web/`.

Contributor faces are defined in the SVG near the end of `index.html`. `main.mjs` shuffles their profiles into the existing equal-size positions on each load; position never reflects commit count.

The hero scene loads three.js, GSAP and ScrollTrigger from jsDelivr at runtime (see the importmap in
`index.html`). They are progressive: if the CDN is unreachable the page renders and works in full without
them, minus the 3D blossom and the scroll choreography. `scene.mjs` also bails out when WebGL2 is absent.

Preview locally:

```sh
python3 -m http.server 8767 --bind 127.0.0.1 --directory website
```

Open `http://127.0.0.1:8767/`. Run the site smoke checks with `node --test website/tests/*.test.mjs` from the repository root. Font licenses are in `assets/fonts/`.

The page's search title, description, and social metadata are in `index.html`. Once the public HTTPS URL is decided, add that URL as the canonical URL and `og:url`, use it for the social image, and put it in a root sitemap for Search Console. Do not use the local preview URL for those tags.

# Guangxing Meat Processing Website

This is a static Cloudflare Pages website. It has no SQL database and does not use Decap CMS.

## Content administration

The `/admin/` page uses a custom password screen. Its Cloudflare Worker reads and writes `data/content.json` through the GitHub Contents API. Each save creates a GitHub commit; Cloudflare Pages then republishes the site automatically.

Deploy `workers/content-admin-worker.js` to the existing `guangxing-admin-auth` Worker and configure:

- Secret `ADMIN_PASSWORD`: a strong password for `/admin/`.
- Secret `GITHUB_TOKEN`: a GitHub fine-grained personal access token restricted to `mishideoo/guangxing` with `Contents: Read and write`.
- Variable `GITHUB_REPO`: `mishideoo/guangxing`.
- Optional variable `ALLOWED_ORIGIN`: `https://guangxing.pages.dev`.

The Worker public URL is configured in `admin/admin.js`. Change `API` there only if the Worker address changes.

## Content and media

- Site information, products, news, and credentials are all in `data/content.json`.
- Product images are under `assets/`. Use absolute site paths such as `/assets/example.jpg` in the content file.
- Upload media through GitHub when needed; the custom admin does not expose a general file uploader.

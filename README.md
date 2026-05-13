# semidesignjobs-blog-images

Public image host for blog posts on [semidesignjobs.com](https://www.semidesignjobs.com/).

## What lives here

WebP files (typically 720–1280px wide, quality 85) used as `<img>` sources inside JobBoardly blog posts. Filenames follow the pattern produced by the `pixabay_images.py` helper in the [semijobengine repo](https://github.com/johnisanerd/semijobengine) (private):

```
<slugified-search-query>_<pixabay-id>.webp
```

For example: `asic-chip-design-silicon_8141642.webp`.

## How it's served

Images are loaded via the standard GitHub raw URL:

```
https://raw.githubusercontent.com/johnisanerd/semidesignjobs-blog-images/main/<filename>.webp
```

The base URL is configured in the main repo's `.env` as `SEMIJOB_IMAGE_BASE_URL`.

## Workflow

The drafting skill in the main repo writes WebP files directly into this clone (configured via `SEMIJOB_IMAGES_DIR`). You commit and push them here separately so they're publicly reachable before the JobBoardly post goes live.

```
cd /Users/johncole/Github/semidesignjobs-blog-images
git add . && git commit -m "Add images for <slug>, <slug>" && git push
```

The publisher in the main repo (`blog/publish_blog.py`) warns when an embedded image hasn't been pushed yet.

## Why a separate repo

The main `semijobengine` repo is private and contains API credentials. Its raw URLs require authentication and won't load in public blog posts. This repo exists purely to serve the image files publicly.

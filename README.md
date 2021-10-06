# Algolia Uploader

![build](https://github.com/wangchucheng/algolia-uploader/workflows/build/badge.svg)
![license](https://img.shields.io/github/license/wangchucheng/algolia-uploader)

Algolia Uploader enables you to update your Algolia index file automatically.

The uploader is largely based on [wangchucheng/algolia-uploader](https://github.com/wangchucheng/algolia-uploader), with the main difference being that we use the `index.replace_all_objects` method instead of `index.save_objects`. See the [Algolia documentation](https://www.algolia.com/doc/api-reference/api-methods/replace-all-objects/?client=python) for more information.

## Try Algolia Uploader

You can use the following example as a template to create a new file with any name under `.github/workflows/`.

```yaml
name: <action_name>

on:
  push:
    branches: [ master ]

jobs:
  upload_algolia_index:
    runs-on: ubuntu-latest
    name: Upload Algolia Index
    steps:
    - uses: actions/checkout@v2
      with:
        fetch-depth: 0
    - uses: tilburgsciencehub/algolia-uploader@master
      with:
        # Algolia app id
        app_id: 02IYLG4AP9
        # Secret token in the organization's 'Setting > Secrets'
        admin_key: ${{ secrets.ALGOLIA_ADMIN_KEY }}
        # The index name
        index_name: tilburgsciencehub
        # The index file path relative to repo root.
        index_file_path: search-index.json
```

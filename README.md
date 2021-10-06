# Algolia Index Updater

Algolia Index Updater enables you to update your Algolia index file automatically.

The updater is largely based on [wangchucheng/algolia-uploader](https://github.com/wangchucheng/algolia-uploader), with the main difference being that we use the `index.replace_all_objects` method instead of `index.save_objects`. Therefore it clears all objects from the index and replaces them with a new set of objects. See the [Algolia documentation](https://www.algolia.com/doc/api-reference/api-methods/replace-all-objects/?client=python) for more information.

## Try Algolia Index Updater

You can use the following example as a template to create a new file with any name under `.github/workflows/`.

```yaml
name: <action_name>

on:
  push:
    branches: [ master ]

jobs:
  upload_algolia_index:
    runs-on: ubuntu-latest
    name: Update Algolia Index
    steps:
    - uses: actions/checkout@v2
      with:
        fetch-depth: 0
    - uses: tilburgsciencehub/algolia-uploader@master
      with:
        # Algolia app id
        app_id: <your_ID>
        # Secret token in the organization's 'Setting > Secrets'
        admin_key: ${{ secrets.ALGOLIA_ADMIN_KEY }}
        # The index name
        index_name: <your_index_name>
        # The index file path relative to repo root.
        index_file_path: search-index.json
```

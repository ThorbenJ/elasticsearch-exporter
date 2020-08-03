elasticsearch-exporter
======================

Export/import elasticsearch indices to/from ndjson files

Requirements
------------

Just ansible.

The exported files could be imported with other tools, such as curl; as they are in the
ndjson format used by the _bulk API.

Role Variables
--------------

- `elex_task`: Set to 'import' or 'export'
  - **Required** always

&nbsp;
- `elex_cloud_id`: The Cloud ID to access (EC, ECE, ECK)
  - **Required** always

&nbsp;
- `elex_cloud_auth`: The Cloud authentication credentials ("username:password")
  - **Required** always

&nbsp;
- `elex_index`: The name of the index to be exported (or was exported, when importing)
  - **Required** always

&nbsp;
- `elex_workdir`: The base directory to store all exports under
  - *Default*: $TMPDIR/elasticsearch_exports

&nbsp;
- `elex_export_date`: Use when importing an 'export' from a past date
  - *Defaults*: Today

&nbsp;
- `elex_target`: The index name to restore an import to
  - *Default*: Same as `elex_index`

&nbsp;
- `elex_restore_aliases`: Restore index aliases when importing
  - *Default*: elex_index == elex_target (i.e. False when importing to a different name)

&nbsp;
The following variables are derived from the ones above, but maybe overridden:

- `elex_elasticsearch_url`: (string) `"https://es.example.com"`
- `elex_login`: (array of two strings) `["username", "password"]`

Dependencies
------------

No other roles

Example Playbook
----------------

See the [tests/test.yml] playbook

License
-------

AGPL 3.0 only

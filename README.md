elasticsearch-exporter
======================

Export/import elasticsearch indices to/from ndjson files

Requirements
------------

Just ansible.

Role Variables
--------------

- `elex_task`: Set to 'import' or 'export'
 - **Required** always

- `elex_cloud_id`: The Cloud ID to access (EC, ECE, ECK)
 - **Required** always
 
- `elex_cloud_auth`: The Cloud authentication credentials ("username:password")
 - **Required** always
 
- `elex_index`: The name of the index to be exported (or was exported, when importing)
 - **Required** always

- `elex_workdir`: The base directory to store all exports under
 - *Default*: $TMPDIR/elasticsearch_exports

- `elex_export_date`: Use when importing an 'export' from a past date
 - *Defaults*: Today
 
- `elex_target`: The index name to restore an import to
 - *Default*: Same as `elex_index`

- `elex_restore_aliases`: Restore index aliases when importing
 - *Default*: elex_index == elex_target (i.e. False when importing to a different name)

The following variables are derived fromt he ones above, but maybe overridden:

- `elex_elasticsearch_url`: (string) `"https://es.example.com"`
- `elex_login`: (array of two strings) `["username", "password"]`
- `elex_datadir`: (string) `workdir/elex_index/elex_export_date`

Dependencies
------------

No other roles

Example Playbook
----------------

See the [test/test.yml] playbook

License
-------

AGPL 3.0 only

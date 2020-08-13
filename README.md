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
  - **Required** always (unless elex_elasticsearch_url is provided)

&nbsp;
- `elex_cloud_auth`: The Cloud authentication credentials ("username:password")
  - **Required** always (unless elex_login is provided)

&nbsp;
- `elex_index`: The index pattern of indices to be exported (or that was exported, when importing)
  - **Required** always
  - Note: When importing this is used has a shell fileglob, to match export directories

&nbsp;
- `elex_workdir`: The base directory to store all exports under
  - *Default*: $TMPDIR/elasticsearch_exports

&nbsp;
- `elex_export_date`: Use when importing an 'export' from a past date
  - *Defaults*: Today

&nbsp;
- `elex_rename`: A RegEx to rename indices on retore. So that you can import to a different name
  - *Default*: Not set
  - *Example*: /^(.*)$/\\1-restored/

&nbsp;
- `elex_restore_aliases`: Restore index aliases when importing
  - *Default*: elex_rename is not defined (i.e. True if not renaming)

&nbsp;
The following variables are derived from the ones above, but maybe overridden:

- `elex_elasticsearch_url`: (string) `"https://es.example.com"` (no tailing /)
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

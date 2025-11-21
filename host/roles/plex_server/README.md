# nerdynik.host plex_server Role

> [!IMPORTANT]
> Please note that this is currently just an initial port from an older collection.
> It has not been yet tested in it's new form.
> However if you do test it and can verify it works as expected. Please open an issue to let me know.

## Role Variables

* ***plex_server_metadir***
  * **Default**: /home/plexdata/Library/Application Support
  * Absolute path to where the Plex Metadata Dir is located.
    This is often called the `Library/Application Support` Directory.
    It's also effectively the config Directory.
* ***plex_server_config_allowed_networks***
  * A comma separated list of IPs or CIDRs of networks allowed to access Plex Server without authentication.
    This can be useful if you are having issues claiming a newly installed Plex Server
    that exists on a separate network then you are attempting to access it from.

## Dependencies

Leverages the role `nerdynik.general.multiplatform_installer` from the `nerdynik.general` collection.

## Role Idempotency

Role is Idempotency

## Author Information

Originally Created by [NerdyNik](https://github.com/nerdynick/)

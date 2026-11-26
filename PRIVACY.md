# Kapacitor on TOS privacy policy

This policy covers the self-hosted TOS package for Kapacitor. The NAS administrator operates the installation and controls its data and backups.

## Data and purpose

Kapacitor receives time-series data and stores tasks, metadata and recorded replays in the TOS data directory mounted at `/var/lib/kapacitor`.

## Sharing and external services

The built-in default InfluxDB connection and usage reporting are disabled in the shipped recipe. If an operator configures an InfluxDB connection, an output or an alert handler, metrics, credentials or alerts can be sent to those selected endpoints.

Installation and updates can contact TOS distribution services and container registries to obtain packages and images. Requests to external services are handled according to the services and locations selected by the operator.

## Retention, access, correction and deletion

Task definitions and recordings persist until removed. Use the Kapacitor CLI or API to list, update and delete tasks and recordings. Retention of source data in external systems is controlled by those systems.

To remove an entire instance, stop it and identify the app-owned storage in Docker Manager before deleting it. The NAS administrator should handle retained backups separately and verify the effects of the TOS uninstall options. Contact the NAS administrator to request access, correction or deletion of data held by the instance.

## Security and support

Use the HTTP API on a trusted network. Protect task files and backups and apply access controls before exposing the service across a trust boundary.

For questions about the TOS package, use the repository's issue tracker. Omit private data, credentials and unredacted logs from public reports.

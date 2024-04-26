# JAMF Protect Pack
----

This pack helps to parse, condition, and set metadata for various sourcetypes of JAMF protect data that comes from MacOS in order to send to something like Splunk.

The pack takes data from an HEC input that has one of the top level sourcetypes and then sorts them into sub-sourcetypes based on their unique format and content.

## HEC Configuration

Ideally this pack is used as a pre-processor in your HEC source, or integrated into your HEC source's pre-processor. You should be passing data to this pack from an HEC token config that pre-sets the sourcetype and index field like so:

```json
{
    "token": "MYTOKENREDACTED",
    "description": "JAMF Protect Telemetry token",
    "allowedIndexesAtToken": [
        "jamf"
    ],
    "metadata": [
        {
            "name": "sourcetype",
            "value": "'jamf:protect:telemetry'"
        },
        {
            "name": "source",
            "value": "'JamfProtect'"
        },
        {
            "name": "index",
            "value": "'jamf'"
        }
    ]
}
```
You would then send your data here, and this pack would transform your data into the subsourcetypes that are possible.

## Sub-Sourcetypes

- `jamf:protect:alerts`
- `jamf:protect:web:traffic`
- `jamf:protect:web:threat`
- `jamf:protect:telemetry:account`
- `jamf:protect:telemetry:audit`
- `jamf:protect:telemetry:auth`
- `jamf:protect:telemetry:disk`
- `jamf:protect:telemetry:exec`
- `jamf:protect:telemetry:internal`
- `jamf:protect:telemetry:interprocess`
- `jamf:protect:telemetry:listen`
- `jamf:protect:telemetry:misc`
- `jamf:protect:telemetry:network`
- `jamf:protect:telemetry:session`
- `jamf:protect:telemetry:time`

## Release Notes

### Version 1.0.0 - 2024-04-28

#### Added

- initial pipeline and docs
- parser with sub-sourcetype extraction and event code lookup

## Contributing to the Pack

To contribute to the Pack, please open an issue on [our github repo](https://github.com/arcsector/jamf_enterprise_source_pack/issues).

## Contact

To contact us please create an issue on [our github repo](https://github.com/arcsector/jamf_enterprise_source_pack/issues)

## License

This Pack uses the [`MIT License`](https://choosealicense.com/licenses/mit/).

# Changelog

## [0.2.8] - 2026-08-01

### Fixed
- feat: add required increment_by to offset pagination (rc17) (#19)

## [0.2.7] - 2026-07-09

### Fixed
- bug: make Wise endpoint definitions pass the schema validator (#18)

## [0.2.6] - 2026-06-30

### Fixed
- feat: rename endpoint files to match endpoint_id (#17)

## [0.2.5] - 2026-06-30

### Fixed
- bug: retrigger version-bump to refresh registry sync (#16)

## [0.2.4] - 2026-06-29

### Fixed
- bug: retrigger version-bump to refresh registry webhook (#15)

## [0.2.3] - 2026-06-29

### Fixed
- bug: fix Wise datetime tz bind and nested-object materialization (#14)

## [0.2.2] - 2026-06-22

### Fixed
- bug: retrigger version-bump to refresh registry webhook (#12)

## [0.2.1] - 2026-05-15

### Fixed
- bug: match Analitiq webhook API Gateway schema exactly (#11)

## [0.2.0] - 2026-04-27

### Added
- feat: add canonical type mapping (#8)

## [0.1.0] - 2026-04-27

### Added
- feat: consolidate manifest into connector.json (#9)

## [0.0.2] - 2026-04-21

### Fixed
- docs: point engine references to analitiq-ai/analitiq-engine (#7)

## [0.0.1] - 2026-03-31

### Added
- Initial connector definition for Wise (formerly TransferWise)
- API key authentication (Personal API Token, Bearer header)
- Post-auth step to select profile (personal or business) via GET /v2/profiles
- Rate limiting configuration: 1000 requests per 60 seconds
- Manifest with placeholder registrations for api_key and profile_id
- Endpoint: GET /v1/profiles -- list user profiles (personal and/or business)
- Endpoint: GET /v1/transfers -- list transfers with offset pagination and date filtering
- Endpoint: GET /v1/accounts -- list recipient (beneficiary) accounts

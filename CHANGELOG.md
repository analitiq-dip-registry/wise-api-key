# Changelog

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

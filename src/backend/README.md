

# Configuration

Configuration uses standard .NET configuration system with convenience environment variable for simpler configuration. 
The convenience environment variable take presidence over other configuration sources. Additional environment variables
can be added by editing the CsrsEnvironmentVariablesConfigurationProvider class.

| Config Path | Environment Variable | Description |
|:---| --- |:---|
| Jwt:Audience | | The client id/resource of the application |
| Jwt:Authority | | The authentication server including the realm, ie https://dev.oidc.gov.bc.ca/auth/realms/onestopauth-basic |
| OAuth:AuthorizationUrl | | |
| OAuth:ResourceUrl | | |
| OAuth:ClientId | | |
| OAuth:Secret | | |
| OAuth:Username | | |
| OAuth:Password | | |
| ApiGateway:BasePath | | |
| Splunk:Url | SPLUNK_URL | The Splunk HEC url |
| Splunk:Token | SPLUNK_TOKEN | The Splunk HEC token |
| Splunk:ValidatServerCertificate | SPLUNK_VALIDATE_SERVER_CERTIFICATE | |
| Tracing:Zipkin:Url | ZIPKIN_URL | Optional Zipkin url, ie http://localhost:9411/api/v2/spans |
| Tracing:Jaeger:Host | JAEGER_HOST | Optional Jaeger host |
| Tracing:Jaeger:Port | JAEGER_PORT | Optional Jaeger port, if not set the default port will be used, 6831 |
| FileManager:Address | | The address for the file manager service, on openshift, it should be dns://service-name.service-namespace.svc:port for service dns based service discovery |
| FileManager:Secure  | | Set to `true` if using https, otherwise `false` |

## User Secrets

Developers can use [User Secrets](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-6.0) in 
their development environment to simplify configuration. For reference, the user secrets for the API project can be found
at this location.

%APPDATA%\Microsoft\UserSecrets\c672e48c-4fbd-4422-9e9e-e36f5e014384

```
dotnet user-secrets set "OAuth:AuthorizationUrl" "https://example.com/adfs/oauth2/token"
dotnet user-secrets set "OAuth:ResourceUrl" "https://example.org/api/data/v9.0"
dotnet user-secrets set "ApiGateway:BasePath" "https://gateway.org/orgname/api/data/v9.0"
dotnet user-secrets set "OAuth:ClientId" "00000000-0000-0000-0000-000000000000"
dotnet user-secrets set "OAuth:Secret" "example-kKgJyRY8QzshrMa82eoHpD9HCKQM8vkx"
dotnet user-secrets set "OAuth:Username" "username"
dotnet user-secrets set "OAuth:Password" "not-really-my-password"
```
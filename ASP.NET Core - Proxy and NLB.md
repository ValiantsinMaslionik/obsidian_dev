#aspnet_core/proxy

---

# Working with proxy and NLB

https://learn.microsoft.com/en-us/aspnet/core/host-and-deploy/proxy-load-balancer?view=aspnetcore-6.0

## Degault proxy for HttpClient 

https://learn.microsoft.com/en-us/dotnet/api/system.net.http.httpclient.defaultproxy?view=net-6.0

The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:

-   HTTP_PROXY: the proxy server used on HTTP requests.
-   HTTPS_PROXY: the proxy server used on HTTPS requests.
-   ALL_PROXY: the proxy server used on HTTP and/or HTTPS requests in case HTTP_PROXY and/or HTTPS_PROXY are not defined.
-   NO_PROXY: a comma-separated list of hostnames that should be excluded from proxying. Asterisks are not supported for wildcards; use a leading dot in case you want to match a subdomain. Examples: `NO_PROXY=.example.com` (with leading dot) will match `www.example.com`, but will not match `example.com`. `NO_PROXY=example.com` (without leading dot) will not match `www.example.com`. This behavior might be revisited in the future to match other ecosystems better.

On systems where environment variables are case-sensitive, the variable names may be all lowercase or all uppercase. The lowercase names are checked first.

The proxy server may be a hostname or IP address, optionally followed by a colon and port number, or it may be an http URL, optionally including a username and password for proxy authentication. The URL must be start with `http`, not `https`, and cannot include any text after the hostname, IP, or port.

## Configure global proxy in IIS-hosted model

web.config
```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath="dotnet" arguments=".\Your.dll" stdoutLogEnabled="false" stdoutLogFile=".\logs\stdout" hostingModel="inprocess">
        <environmentVariables>
          <environmentVariable name="http_proxy" value="http://yourproxy.ins.local"/>
          <environmentVariable name="https_proxy" value="http://yourproxy.ins.local"/>
          <environmentVariable name="no_proxy" value=".local,.applicationinsights.azure.com,.applicationinsights.microsoft.com,.services.visualstudio.com"/>
        </environmentVariables>
      </aspNetCore>
    </system.webServer>
  </location>
</configuration>
```


## Logging with ILogger
As an alternative to `TraceWriter`, an instance of [ILogger](https://docs.microsoft.com/en-us/aspnet/core/api/microsoft.extensions.logging.ilogger) can be used instead.

The advantage of using an ILogger instead of a `TraceWriter` is that you will get support for structured logging which allows for richer analytics support. This is helpul if you target your logs at a tool like [Application Insights](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-analytics).


```csharp
[FunctionName("ILoggerHttpLogging")]
public static HttpResponseMessage Run([HttpTrigger(AuthorizationLevel.Anonymous, "GET")]HttpRequestMessage req, ILogger log)
{
    log.LogInformation("101 Azure Function Demo - Logging with ITraceWriter");
    log.LogTrace("Here is a verbose log message");
    log.LogWarning("Here is a warning log message");
    log.LogError("Here is an error log message");
    log.LogCritical("This is a critical log message => {message}", "We have a big problem");

    return req.CreateResponse(HttpStatusCode.OK);
}

```

[!include[](../includes/takeaways-heading.md)]
* `ILogger` can be used as an alternative to `TraceWriter`
* `ILogger` supports structured logging

[!include[](../includes/read-more-heading.md)]
* [ILogger support](https://github.com/Azure/azure-webjobs-sdk-script/wiki/ILogger)
* [ILogger extension methods](https://docs.microsoft.com/en-us/aspnet/core/api/microsoft.extensions.logging.loggerextensions#methods_summary)
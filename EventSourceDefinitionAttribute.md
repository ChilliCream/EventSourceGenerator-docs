# Custom Event Source Definition Attribute

If you don't want another package dependency in your project just to have the ```EventSourceDefinitionAttribute``` to mark your event source interfaces as relevant for esgen you can opt to add your own attribute to your project. The attribute can be public or internal and has to have the following structure:

```csharp
/// <summary>
/// Allows the event tracing for Windows (ETW) name to be defined independently of the name of
/// the event source interface.
/// </summary>
[AttributeUsage(AttributeTargets.Interface, AllowMultiple = false, Inherited = false)]
internal sealed class EventSourceDefinitionAttribute
    : Attribute
{
    /// <summary>
    /// Gets or sets the event source identifier.
    /// </summary>
    public string Guid { get; set; }

    /// <summary>
    /// Gets or sets the name of the localization resource file.
    /// </summary>
    public string LocalizationResources { get; set; }

    /// <summary>
    /// Gets or sets the name of the event source.
    /// </summary>
    public string Name { get; set; }
}
```
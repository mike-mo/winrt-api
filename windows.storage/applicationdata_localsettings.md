---
-api-id: P:Windows.Storage.ApplicationData.LocalSettings
-api-type: winrt property
---

<!-- Property syntax
public Windows.Storage.ApplicationDataContainer LocalSettings { get; }
-->

# Windows.Storage.ApplicationData.LocalSettings

## -description
Gets the application settings container in the local app data store.

## -property-value
The application settings container.

## -remarks
For both [LocalSettings](applicationdata_localsettings.md) and [RoamingSettings](applicationdata_roamingsettings.md), the name of each setting can be 255 characters in length at most. Each setting can be up to 8K bytes in size and each composite setting can be up to 64K bytes in size.

The [Windows Runtime data types](http://msdn.microsoft.com/library/b5735851-ec07-48c1-92b4-ca9f768096f6) are supported for app settings.

## -examples
Use the [LocalSettings | localSettings](applicationdata_localsettings.md) property to get the settings in an [ApplicationDataContainer](applicationdatacontainer.md) object. Use the [ApplicationDataContainer.Values | values](applicationdatacontainer_values.md) property to access the settings in the `localSettings` container. This example creates and reads a setting named `exampleSetting`.

Call the [ApplicationDataContainerSettings.Remove | remove](applicationdatacontainersettings_remove.md) method to delete the `exampleSetting` setting when you have finished with it.

Note that to access the [RoamingSettings](applicationdata_roamingsettings.md), use the same process outlined in the example, except change the occurrences of `localSettings` to `roamingSettings`

```javascript
var applicationData = Windows.Storage.ApplicationData.current;

var localSettings = applicationData.localSettings;

// Create a simple setting

localSettings.values["exampleSetting"] = "Hello Windows";

// Read data from a simple setting

var value = localSettings.values["exampleSetting"];
        
if (!value)
{
    // No data
}
else
{
    // Access data in value
}

// Delete a simple setting

localSettings.values.remove("exampleSetting");
```

```csharp
var localSettings = Windows.Storage.ApplicationData.Current.LocalSettings;

// Create a simple setting

localSettings.Values["exampleSetting"] = "Hello Windows";

// Read data from a simple setting

Object value = localSettings.Values["exampleSetting"];

if (value == null)
{
    // No data
}
else
{
    // Access data in value
}

// Delete a simple setting

localSettings.Values.Remove("exampleSetting");
```

```vb
Dim localSettings As Windows.Storage.ApplicationDataContainer = Windows.Storage.ApplicationData.Current.LocalSettings

' Create a simple setting

localSettings.Values("exampleSetting") = "Hello Windows";

' Read data from a simple setting

Dim value As Object = localSettings.Values("exampleSetting")

If value Is Nothing Then
   ' No data
Else
   ' Access data in value
End If

' Delete a simple setting

localSettings.Values.Remove("exampleSetting")
```

```cpp
ApplicationDataContainer^ localSettings = ApplicationData::Current->LocalSettings;

// Create a simple setting

auto values = localSettings->Values;
values->Insert("exampleSetting", dynamic_cast<PropertyValue^>(PropertyValue::CreateString("Hello Windows")));

// Read data from a simple setting

auto values = localSettings->Values;
String^ value = safe_cast<String^>(localSettings->Values->Lookup("exampleSetting"));

if (!value)
{
    // No data
}
else
{
    // Access data in value
}

// Delete a simple setting

values->Remove("exampleSetting");
```



## -see-also
[Quickstart: Local application data (JavaScript)](http://msdn.microsoft.com/library/87dfe8e5-2d01-45cf-bcb1-25f54219a439), [Store and retrieve settings and other app data](http://msdn.microsoft.com/library/41676a02-325a-455e-8565-c9ec0bc3a8fe), [Store and retrieve settings and other app data](http://msdn.microsoft.com/library/41676a02-325a-455e-8565-c9ec0bc3a8fe), [Content indexer sample (Windows 10)](http://go.microsoft.com/fwlink/p/?LinkId=620524)
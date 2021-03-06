# PermissionPlugin
A set of tools for Unity to allow handling Permission for Android and iOS.

# Install
PermissionPlugin.unitypackage

# Usage
```cs
using Permission;
```

#### Example: Check permissions.
```cs
public IEnumerator Example()
{
  yield return PermissionPlugin.Check(PermissionType.Camera, result =
  {
    Debug.Log(result);
  });
}
```

#### Example: Request permission.
```cs
public IEnumerator Example()
{
  yield return PermissionPlugin.Request(PermissionType.Camera, result =>
  {
    Debug.Log(result);
  });
}
```

#### Example: Open permission setting screen.
```cs
public void Example()
{
  PermissionPlugin.Open(PermissionType.Camera);
}
```

# AndroidManifest.xml
Replace main Activity.
```xml
<!--
<activity android:name="com.unity3d.player.UnityPlayerActivity" ...
-->
<activity android:name="com.hiyorin.permission.CustomUnityPlayerActivity" ...
```

# When using your own UnityPlayerActivity
Please pass the value of OnRequestPermissionsResult of your Activity
```cs
public void Exapmle(int requestCode, string[] permissions, int[] grantResults)
{
  PermissionPlugin.AndroidRequestPermissionsResult(requestCode, permissions, grantResults);
}
```

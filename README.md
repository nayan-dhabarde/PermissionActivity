# Permission Activity

The current way of handling runtime permissions in Android is error prone and needs a lot of boilerplate code.
Permission Activity makes it easy to handle runtime permissions using Higher order functions and by maintaining a map of your permissions to actions.
To use it, all you need to do is to inherit the PermissionActivity class and then call requestPermission(permission = permission in form of array, action = { }).


## How to use:
1. Add jitpack io to project level build.gradle file:

```Groovy
    allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
    }
```

2. Add Permission activity dependency in app level build.gradle file:

```Groovy
    implementation 'com.github.ndhabrde11:PersmissionActivity:1.0.0'
```


## Sample code:
```kotlin
class MainActivity : PermissionActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        requestPermission(arrayOf(android.Manifest.permission.CAMERA)) { status ->
            when(status) {
                Status.REQUESTING -> {}
                Status.GRANTED -> {
                    // do your stuff
                }
                Status.DENIED -> {
                    // show message
                }
            }
        }
    }
}
```

That's it!

## Logging
Following are the logs provided by the library:
``` D/PermissionActivity: CAMERA: Requesting permission ```
``` D/PermissionActivity: CAMERA: Permission granted ```
``` D/PermissionActivity: CAMERA: Permission denied ```

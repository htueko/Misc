### custom_view.xml
```xml
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    tools:context=".MainActivity">
 
    <Button
        android:id="@+id/btnShowAlert"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Show Alert"/>
 
</LinearLayout>
```

### alert_dialog.kt
```kotlin
import android.support.v7.app.AppCompatActivity
import android.os.Bundle
import kotlinx.android.synthetic.main.activity_main.*
import android.app.AlertDialog
import android.content.DialogInterface
 
class MainActivity : AppCompatActivity() {
 
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
 
        // when button is clicked, show the alert
        btnShowAlert.setOnClickListener {
            // build alert dialog
            val dialogBuilder = AlertDialog.Builder(this)
 
            // set message of alert dialog
            dialogBuilder.setMessage("Do you want to close this application ?")
                    // if the dialog is cancelable
                    .setCancelable(false)
                    // positive button text and action
                    .setPositiveButton("Proceed", DialogInterface.OnClickListener {
                        dialog, id -> finish()
                    })
                    // negative button text and action
                    .setNegativeButton("Cancel", DialogInterface.OnClickListener {
                        dialog, id -> dialog.cancel()
                    })
 
            // create dialog box
            val alert = dialogBuilder.create()
            // set title for alert dialog box
            alert.setTitle("AlertDialogExample")
            // show alert dialog
            alert.show()
        }
    }
} 
```

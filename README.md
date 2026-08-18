# Ex.No:3 Develop a simple application to play and control the audio file in android studio.


## AIM:

To develop a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as audiofile and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml and create start,pause and stop button.

Step 6: Display message give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
Program to play and control the audio file”.
Developed by: NITHISH S
Registeration Number : 212223220070
```
Main_Activity.java
```
package com.example.audioplayer;

import android.media.MediaPlayer;
import android.os.Bundle;
import android.util.Log;
import android.widget.Button;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {
    private static final String TAG = "MainActivity";
    private MediaPlayer mediaPlayer;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

        Button btnPlay = findViewById(R.id.btnPlay);
        Button btnPause = findViewById(R.id.btnPause);
        Button btnStop = findViewById(R.id.btnStop);

        // Initialize MediaPlayer
        // Note: You must place an audio file named 'audio.mp3' (or similar)
        // in 'app/src/main/res/raw/' for the app to play music.
        int audioResId = getResources().getIdentifier("audio", "raw", getPackageName());

        if (audioResId != 0) {
            mediaPlayer = MediaPlayer.create(this, audioResId);
        } else {
            Toast.makeText(this, "Audio file not found in res/raw/", Toast.LENGTH_LONG).show();
            Log.e(TAG, "Audio resource 'res/raw/audio' not found.");
        }

        btnPlay.setOnClickListener(v -> {
            if (mediaPlayer != null && !mediaPlayer.isPlaying()) {
                mediaPlayer.start();
            }
        });

        btnPause.setOnClickListener(v -> {
            if (mediaPlayer != null && mediaPlayer.isPlaying()) {
                mediaPlayer.pause();
            }
        });

        btnStop.setOnClickListener(v -> {
            if (mediaPlayer != null) {
                mediaPlayer.stop();
                try {
                    mediaPlayer.prepare();
                } catch (Exception e) {
                    Log.e(TAG, "Error preparing MediaPlayer", e);
                }
            }
        });
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        if (mediaPlayer != null) {
            mediaPlayer.release();
            mediaPlayer = null;
        }
    }
}
```
Activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="40dp"
        android:text="@string/app_title"
        android:textSize="28sp"
        android:textStyle="bold" />

    <LinearLayout
        style="?android:attr/buttonBarStyle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btnPlay"
            style="?android:attr/buttonBarButtonStyle"
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:layout_margin="8dp"
            android:text="@string/btn_play" />

        <Button
            android:id="@+id/btnPause"
            style="?android:attr/buttonBarButtonStyle"
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:layout_margin="8dp"
            android:text="@string/btn_pause" />

        <Button
            android:id="@+id/btnStop"
            style="?android:attr/buttonBarButtonStyle"
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:layout_margin="8dp"
            android:text="@string/btn_stop" />
    </LinearLayout>

</LinearLayout>
```


## OUTPUT

<img width="1917" height="1014" alt="image_4" src="https://github.com/user-attachments/assets/80246ba7-cb49-4a86-9516-19b18e5aa9e9" />



## RESULT
   Thus a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio is developed and executed successfully.

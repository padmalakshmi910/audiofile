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

# MainActivity.java

```

package com.example.audioplayer;

import android.media.MediaPlayer;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private MediaPlayer mediaPlayer;
    private Button btnPlay, btnPause, btnStop;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btnPlay = findViewById(R.id.btnPlay);
        btnPause = findViewById(R.id.btnPause);
        btnStop = findViewById(R.id.btnStop);

        mediaPlayer = MediaPlayer.create(this, R.raw.audio);

        btnPlay.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer == null) {
                    mediaPlayer = MediaPlayer.create(
                            MainActivity.this, R.raw.audio);
                }
                if (!mediaPlayer.isPlaying()) {
                    mediaPlayer.start();
                }
            }
        });

        btnPause.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null && mediaPlayer.isPlaying()) {
                    mediaPlayer.pause();
                }
            }
        });

        btnStop.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null) {
                    mediaPlayer.stop();
                    mediaPlayer.release();
                    mediaPlayer = null;
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

# activity_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Audio Player"
        android:textSize="28sp"
        android:textStyle="bold"
        android:layout_marginBottom="40dp"/>

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btnPlay"
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:text="Play"
            android:layout_margin="8dp"/>

        <Button
            android:id="@+id/btnPause"
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:text="Pause"
            android:layout_margin="8dp"/>

        <Button
            android:id="@+id/btnStop"
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:text="Stop"
            android:layout_margin="8dp"/>

    </LinearLayout>

</LinearLayout>

```

## OUTPUT

<img width="340" height="741" alt="image" src="https://github.com/user-attachments/assets/af659ad7-a799-438c-a1d2-e2191a114faf" />

## RESULT

   Thus a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio is developed and executed successfully.

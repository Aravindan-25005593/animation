# Ex.No: 11 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:



## PROGRAM:
```
/*
Program to display animation operation”.
Developed by: ARAVINDAN SD
Registeration Number : 212224243001
*/
```
Activity_main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/purple"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_marginTop="32dp"
        android:src="@drawable/ic_star"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:padding="16dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageView">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal">

            <Button
                android:id="@+id/btnMove"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:layout_margin="12dp"
                android:textSize="12sp"
                android:insetTop="0dp"
                android:insetBottom="0dp"
                app:cornerRadius="50dp"
                android:backgroundTint="@color/grey"
                android:text="Move" />

            <Button
                android:id="@+id/btnBlink"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:layout_margin="12dp"
                android:textSize="12sp"
                android:insetTop="0dp"
                android:insetBottom="0dp"
                app:cornerRadius="50dp"
                android:backgroundTint="@color/grey"
                android:text="Blink" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal">

            <Button
                android:id="@+id/btnFade"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:layout_margin="12dp"
                android:textSize="12sp"
                android:insetTop="0dp"
                android:insetBottom="0dp"
                app:cornerRadius="50dp"
                android:backgroundTint="@color/grey"
                android:text="Fade" />

            <Button
                android:id="@+id/btnClockwise"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:layout_margin="12dp"
                android:textSize="12sp"
                android:insetTop="0dp"
                android:insetBottom="0dp"
                app:cornerRadius="50dp"
                android:backgroundTint="@color/grey"
                android:text="Clockwise" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal">

            <Button
                android:id="@+id/btnZoom"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:layout_margin="12dp"
                android:textSize="12sp"
                android:insetTop="0dp"
                android:insetBottom="0dp"
                app:cornerRadius="50dp"
                android:backgroundTint="@color/grey"
                android:text="Zoom" />

            <Button
                android:id="@+id/btnSlide"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:layout_margin="12dp"
                android:textSize="12sp"
                android:insetTop="0dp"
                android:insetBottom="0dp"
                app:cornerRadius="50dp"
                android:backgroundTint="@color/grey"
                android:text="Slide" />
        </LinearLayout>

    </LinearLayout>

</androidx.constraintlayout.widget.ConstraintLayout>
```
MainActivity.java:
```
package com.example.animations;

import android.os.Bundle;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    private ImageView imageView;

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

        imageView = findViewById(R.id.imageView);

        Button btnMove = findViewById(R.id.btnMove);
        Button btnBlink = findViewById(R.id.btnBlink);
        Button btnFade = findViewById(R.id.btnFade);
        Button btnClockwise = findViewById(R.id.btnClockwise);
        Button btnZoom = findViewById(R.id.btnZoom);
        Button btnSlide = findViewById(R.id.btnSlide);

        btnMove.setOnClickListener(v -> startAnimation(R.anim.move));
        btnBlink.setOnClickListener(v -> startAnimation(R.anim.blink));
        btnFade.setOnClickListener(v -> startAnimation(R.anim.fade));
        btnClockwise.setOnClickListener(v -> startAnimation(R.anim.clockwise));
        btnZoom.setOnClickListener(v -> startAnimation(R.anim.zoom));
        btnSlide.setOnClickListener(v -> startAnimation(R.anim.slide));
    }

    private void startAnimation(int animResource) {
        Animation animation = AnimationUtils.loadAnimation(getApplicationContext(), animResource);
        imageView.startAnimation(animation);
    }
}
```
AndroidManifest.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Animations">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```
##anim:
blink.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <alpha
        android:duration="300"
        android:fromAlpha="0.0"
        android:interpolator="@android:anim/accelerate_interpolator"
        android:repeatCount="infinite"
        android:repeatMode="reverse"
        android:toAlpha="1.0" />
</set>
```
clockxml:
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true">
    <rotate
        android:duration="1000"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toDegrees="360" />
</set>
```
fade.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true">
    <alpha
        android:duration="1000"
        android:fromAlpha="1.0"
        android:toAlpha="0.0" />
</set>
```
move.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true">
    <translate
        android:duration="1000"
        android:fromXDelta="0%"
        android:fromYDelta="0%"
        android:toXDelta="50%"
        android:toYDelta="50%" />
</set>
```
slide.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true">
    <translate
        android:duration="1000"
        android:fromXDelta="0%"
        android:toXDelta="100%" />
</set>
```
## OUTPUT

<img width="1919" height="1198" alt="image" src="https://github.com/user-attachments/assets/b939d43c-909f-4650-a9d2-3098f974cdb3" />
<img width="1344" height="2992" alt="Screenshot_20260317_135107" src="https://github.com/user-attachments/assets/e2a02b94-cad0-4b30-a324-106cdecb5e3c" />
<img width="1344" height="2992" alt="Screenshot_20260317_135210" src="https://github.com/user-attachments/assets/b5fae8ba-0f84-4632-a0af-c9c6384aa220" />

## RESULT

The Android image is Animation app was succesfully developed to perform Move,blink,fade,clockwise,zoom,slide operations

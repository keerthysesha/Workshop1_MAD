# Workshop1_MAD

# PROGRAM:

## ActivityManifest.xml:
```
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="com.example.workshop1_explicit_intend">
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/Theme.Workshop1_Explicit_Intend"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity android:name=".MainActivity2"></activity>
    </application>

</manifest>
```
## MainActivity.java:
```
package com.example.workshop1_explicit_intend;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

import android.content.Intent;

import android.view.View;
import android.widget.Button;
import android.widget.EditText;



public class MainActivity extends AppCompatActivity {

    EditText editTextName, editTextAge, editTextEmail, editTextContact;
    Button buttonSubmit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editTextName = findViewById(R.id.editTextName);
        editTextAge = findViewById(R.id.editTextAge);
        editTextEmail = findViewById(R.id.editTextEmail);
        editTextContact = findViewById(R.id.editTextContact);
        buttonSubmit = findViewById(R.id.buttonSubmit);

        buttonSubmit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String name = editTextName.getText().toString();
                int age = Integer.parseInt(editTextAge.getText().toString());
                String email = editTextEmail.getText().toString();
                String contact = editTextContact.getText().toString();

                Intent intent = new Intent(MainActivity.this, MainActivity2.class);
                intent.putExtra("NAME", name);
                intent.putExtra("AGE", age);
                intent.putExtra("EMAIL", email);
                intent.putExtra("CONTACT", contact);
                startActivity(intent);
            }
        });
    }
}
```
## Activity_main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/editTextName"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:hint="Enter Name"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <EditText
        android:id="@+id/editTextAge"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:hint="Enter Age"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextName" />

    <EditText
        android:id="@+id/editTextEmail"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:hint="Enter Email"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextAge" />

    <EditText
        android:id="@+id/editTextContact"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:hint="Enter Contact Number"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextEmail" />

    <Button
        android:id="@+id/buttonSubmit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Submit"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.5"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextContact" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
## MainActivity.java:
```
package com.example.workshop1_explicit_intend;

import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity2 extends AppCompatActivity {

    TextView textViewName, textViewAge, textViewEmail, textViewContact;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        textViewName = findViewById(R.id.textViewName);
        textViewAge = findViewById(R.id.textViewAge);
        textViewEmail = findViewById(R.id.textViewEmail);
        textViewContact = findViewById(R.id.textViewContact);

        Intent intent = getIntent();
        if (intent != null) {
            String name = intent.getStringExtra("NAME");
            int age = intent.getIntExtra("AGE", 0);
            String email = intent.getStringExtra("EMAIL");
            String contact = intent.getStringExtra("CONTACT");

            textViewName.setText("Name: " + name);
            textViewAge.setText("Age: " + age);
            textViewEmail.setText("Email: " + email);
            textViewContact.setText("Contact Number: " + contact);
        }
    }
}
```
## Activity_main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/textViewName"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Name: "
        android:textSize="20sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textViewAge"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Age: "
        android:textSize="20sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textViewName" />

    <TextView
        android:id="@+id/textViewEmail"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Email: "
        android:textSize="20sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textViewAge" />

    <TextView
        android:id="@+id/textViewContact"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Contact Number: "
        android:textSize="20sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textViewEmail" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

# OUTPUT:

![Screenshot 2024-03-20 144348](https://github.com/keerthysesha/Workshop1_MAD/assets/125575936/78d7ca05-6357-46cd-a81e-fe30659b6606)

![Screenshot 2024-03-20 144549](https://github.com/keerthysesha/Workshop1_MAD/assets/125575936/8ca46fb7-742d-446c-a6ac-3a26f731b045)

![Screenshot 2024-03-20 144611](https://github.com/keerthysesha/Workshop1_MAD/assets/125575936/b988b5da-1e5c-46d0-af92-446f5644b93b)

![1](https://github.com/keerthysesha/Workshop1_MAD/assets/125575936/97eabb17-deb8-48a8-bece-f4be6be46a49)

![2](https://github.com/keerthysesha/Workshop1_MAD/assets/125575936/bbe3ea79-00e3-44e9-ba8b-6a7c566f2b16)

![3](https://github.com/keerthysesha/Workshop1_MAD/assets/125575936/8cb172f1-b139-468e-aaf4-8317192017ec)

package com.ktds.myintent;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private Button btnNewActivity;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btnNewActivity = (Button) findViewById(R.id.btnNewActivity);
        btnNewActivity.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(MainActivity.this, SubActivity.class );
                startActivity(intent);
            }
        });
    }

    private  long pressedTime = 0L;
    @Override
    public void onBackPressed() {

        if ( System.currentTimeMillis() > pressedTime + 2000) {
            pressedTime = System.currentTimeMillis();
            Toast.makeText(this, "한번 더 누르면 종료됩니다.", Toast.LENGTH_LONG).show();
        }
        else {
            super.onBackPressed();
        }
    //2초 이내에 백버튼을 다시 누르면 종료, 아니면 무시함.

    }
}

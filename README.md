# Mobile
모바일프로그래밍



package com.cookandroid.myapplication;

import android.os.Bundle;
import android.view.MotionEvent;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    
    //클래스 객체 만들고
    EditText Edit1, Edit2;
    Button btnAdd, btnSub, btnMul, btnDiv;

    TextView textResult;
    String num1, num2;
    Integer result;
    Button[] numButtons = new Button[10];
    Integer[] numBtnIDs = {R.id.btn0, R.id.btn1, R.id.btn2, R.id.btn3, R.id.btn4, R.id.btn5,
            R.id.btn6, R.id.btn7, R.id.btn8, R.id.btn9};
    int i;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main4);

        setTitle("테이블레이아웃 계산기");

        //id 할당
        Edit1 = (EditText) findViewById(R.id.Edit1);
        Edit2 = (EditText) findViewById(R.id.Edit2);

        btnAdd = (Button) findViewById(R.id.BtnAdd);
        btnSub = (Button) findViewById(R.id.BtnSub);
        btnMul = (Button) findViewById(R.id.BtnMul);
        btnDiv = (Button) findViewById(R.id.BtnDiv);

        textResult = (TextView) findViewById(R.id.Textresult);

        //이벤트 리스너

        btnAdd.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View arg0, MotionEvent arg1) {
                num1 = Edit1.getText().toString();
                num2 = Edit2.getText().toString();
                result = Integer.parseInt(num1) + Integer.parseInt(num2);
                textResult.setText("계산결과" + result.toString());
                return false;
            }
        });
        btnSub.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View arg0, MotionEvent arg1) {
                num1 = Edit1.getText().toString();
                num2 = Edit2.getText().toString();
                result = Integer.parseInt(num1) - Integer.parseInt(num2);
                textResult.setText("계산결과" + result.toString());
                return false;
            }
        });
        btnMul.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View arg0, MotionEvent arg1) {
                num1 = Edit1.getText().toString();
                num2 = Edit2.getText().toString();
                result = Integer.parseInt(num1) * Integer.parseInt(num2);
                textResult.setText("계산결과" + result.toString());
                return false;
            }
        });
        btnDiv.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View arg0, MotionEvent arg1) {
                num1 = Edit1.getText().toString();
                num2 = Edit2.getText().toString();
                result = Integer.parseInt(num1) / Integer.parseInt(num2);
                textResult.setText("계산결과" + result.toString());
                return false;
            }
        });

        for (i = 0; i < numBtnIDs.length; i++) {
            numButtons[i] = (Button) findViewById(numBtnIDs[i]);
        }
        for (i = 0; i < numBtnIDs.length; i++) {
            final int index;
            index = 1;
            numButtons[index].setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    if (Edit1.isFocused() == true) {
                        num1 = Edit1.getText().toString() + numButtons[index].getText().toString();
                        Edit1.setText(num1);
                    } else if (Edit2.isFocused() == true) {
                        num2 = Edit2.getText().toString() + numButtons[index].getText().toString();
                        Edit2.setText(num2);

                    } else {
                        Toast.makeText(getApplicationContext(),
                                "먼저 에디터 텍스틀 선택하세요.", Toast.LENGTH_SHORT).show();
                    }
                }
            });
        }
    }
}

---

xml 파일

---


<?xml version="1.0" encoding="utf-8"?>
<TableLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_margin="10dp"
    android:background="#F8FCFF"
    android:orientation="horizontal"
    tools:context=".MainActivity4">

    <TableRow
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:paddingTop="10dp"
        android:paddingBottom="10dp">

        <EditText
            android:id="@+id/Edit1"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:layout_span="5"
            android:layout_weight="1"
            android:ems="10"
            android:inputType="text"
            android:text="Name" />

    </TableRow>

    <TableRow
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:paddingTop="10dp"
        android:paddingBottom="10dp">

        <EditText
            android:id="@+id/Edit2"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_span="5"
            android:layout_weight="1"
            android:ems="10"
            android:inputType="text"
            android:paddingTop="10dp"
            android:paddingBottom="10dp"
            android:text="Name" />

    </TableRow>

    <TableRow
        android:layout_width="359dp"
        android:layout_height="wrap_content">

        <Button
            android:id="@+id/btn0"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_span="1"
            android:layout_weight="1"
            android:text="0" />

        <Button
            android:id="@+id/btn1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_span="1"
            android:layout_weight="1"
            android:text="1" />

        <Button
            android:id="@+id/btn2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_span="1"
            android:layout_weight="1"
            android:text="2" />

        <Button
            android:id="@+id/btn3"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"

            android:layout_span="1"
            android:layout_weight="1"
            android:text="3" />

        <Button
            android:id="@+id/btn4"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_span="1"
            android:layout_weight="1"
            android:text="4" />
    </TableRow>

    <TableRow
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <Button
            android:id="@+id/btn5"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="5" />

        <Button
            android:id="@+id/btn6"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="6" />

        <Button
            android:id="@+id/btn7"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="7" />

        <Button
            android:id="@+id/btn8"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="8" />

        <Button
            android:id="@+id/btn9"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="9" />

    </TableRow>

    <TableRow
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical"
        android:paddingTop="10dp"
        android:paddingBottom="10dp">

        <Button
            android:id="@+id/BtnAdd"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="20dp"
            android:layout_marginBottom="20dp"
            android:layout_weight="5"
            android:text="더하기" />

    </TableRow>

    <TableRow
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical"
        android:paddingTop="10dp"
        android:paddingBottom="10dp">

        <Button
            android:id="@+id/BtnSub"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="20dp"
            android:layout_marginBottom="20dp"
            android:layout_weight="1"
            android:text="빼기" />

    </TableRow>

    <TableRow
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical"
        android:paddingTop="10dp"
        android:paddingBottom="10dp">

        <Button
            android:id="@+id/BtnMul"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="20dp"
            android:layout_marginBottom="20dp"
            android:layout_weight="1"
            android:text="곱하기" />

    </TableRow>

    <TableRow
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical"
        android:paddingTop="10dp"
        android:paddingBottom="10dp">

        <Button
            android:id="@+id/BtnDiv"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="20dp"
            android:layout_marginBottom="20dp"
            android:layout_weight="1"
            android:text="나누기" />

    </TableRow>

    <TableRow
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <TextView
            android:id="@+id/Textresult"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="계산결과:"
            android:textSize="20sp" />
    </TableRow>

</TableLayout>


모바일 프로그래밍 

에뮬레이터(AVD) - 설치
2.안드로이드의 구조 ( 응용프로그램-> 응용 프로그램 프레임워크 ->안드로이드 런타임 -> 라이브러리 ->리눅스 커널 ( 안로이드 개요 PDF 25장)
3.프로젝트에서 사용되는 폴더용도 
    java폴더(주로 엑티비티에서 할일 프로그래밍)/
    res폴더 사용되는 이미지 레이아웃 문자열등이 들어가는 폴더
        layout폴더 엑티비티(화면) 구성하는 xml <- 메인화면 구성 ★
        values폴더 문자열을 저장하는 String.xml 컬러를 저장하는 color.xml등이 들어감
        menu폴더 메뉴 XML 파일이 저장됨
    manifests폴더 AndriodeManifest 파일이 들어가있음
    Garle Scripts폴더 build 스크립트 핵심파일이 들어감 SDK JVM등 설정 되어있음
int apple[][] = new int[3,4] 배열객체 만들떄
int apple[] = {1,2,3} 배열애 리스트 넣을떄
4,오버로딩(같은이름 다른타입 메서드 적용) , 오버 라이딩(부모클래스를 재정의해서 사용) 

(기본적인 JAVA 프로그래밍 구조 )
1.변수선언
체크박스대입
체크박스대입하는 클래스 정의

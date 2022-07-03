# 코틀린으로 웹뷰 구현하기

## 01. 웹앱 테스트 gif
#### <수정이 필요한 사항>
- 프로젝트 이름이 상단바에 보이지 않아야 함.
- 웹앱 사용할 때 새 창 열리지 않게 수정 필요

![webview_Test](https://user-images.githubusercontent.com/96757866/177026875-bc7ddd0b-b167-4a93-9338-eea5a3b3ec8c.gif)

## 02. 웹뷰 설정하기
- 블로그 검색하면 상당히 많은 자료가 나옴
- 하지만 대부분 최신 자료가 아니기 때문에 코드가 먹히지 않음
- 공식 문서 참고
### (1) 웹뷰 사용을 위한 Manifest 권한 설정
```
<uses-permission android:name="android.permission.INTERNET" />
```
![web01](https://user-images.githubusercontent.com/96757866/177027905-1fbe8572-1da2-4012-8f0f-3c864d00f897.png)

- application 설정 (생략함)
```
android:usesCleartextTraffic="true"
```
- 웹 랜딩 속도 및 성능 향상 설정 (생략함)
```
android:hardwareAccelerated="true"
```

### (2) activity_main.xml 설정
- TextView 삭제
- widgets의 Webview 끌어오기
- 가로, 세로 match_parent 설정
- id 지정
![web02](https://user-images.githubusercontent.com/96757866/177028275-ba11547a-7826-4617-ad21-bed10088d5da.png)
```
<WebView
        android:id="@+id/main_webview"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
```

### (3) MainActivity.kt
![web03](https://user-images.githubusercontent.com/96757866/177028361-31aff1ea-24e0-4bf3-8550-1988d2d833c2.png)

```
val myWebView: WebView = findViewById(R.id.main_webview)
        myWebView.loadUrl("https://www.google.com")
```


## Reference
- https://developer.android.com/guide/webapps/webview#kotlin

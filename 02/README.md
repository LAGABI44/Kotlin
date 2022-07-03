# 웹뷰 확장(상단바 없애기, 새창 열리지 않게)

## 01. 웹앱 테스트 gif
### <수정이 필요한 사항>
- 모바일 사이트가 아닌 일반 사이트로 등록시 생기는 오류 해결
- 메인페이지의 검색 외 기능도 작동할 수 있게 설정

### (1) https://www.google.com
![webview_Test2](https://user-images.githubusercontent.com/96757866/177030936-b1f82a17-aec9-4206-9e32-8062e90c6394.gif)

### (2) https://m.naver.com
- 메인 페이지에서 검색창까진 잘 됨
- 다른 아이콘을 선택할 때 전혀 작동하지 않음을 발견   
        => 아마 url 이 달라져서..라고 추정   
        
![naver_test](https://user-images.githubusercontent.com/96757866/177031456-4549f75d-1a70-4989-8447-c39a4b698e56.gif)

- https://www.naver.com 으로 할 시 오류 발생
- 해결방법 [참고](https://nobase-dev.tistory.com/81)하기
<img src="https://user-images.githubusercontent.com/96757866/177031469-61185106-78cb-4980-a430-3a5b946ca866.jpg" width="300"/>

## 02. 웹뷰 설정하기

### (1) 프로젝트 이름 제거
- res/values/themes.xml 에 코드 추가
![webview01](https://user-images.githubusercontent.com/96757866/177030854-359b6b27-bca6-4194-95ac-0bef7d0b9a79.png)
```
<item name="windowNoTitle">true</item>
```


### (2) 새창 열리지 않게 설정
- MainActivity.kt 설정
![webview02](https://user-images.githubusercontent.com/96757866/177030873-5197a680-57ca-493b-91a3-6f7d456cbcfe.png)

```
myWebView.webViewClient = WebViewClient()
```

### (3) 뒤로가기 설정
![webview01](https://user-images.githubusercontent.com/96757866/177030877-70be62e4-a3d3-44b8-9ee3-cf639853643b.png)

```
override fun onKeyDown(keyCode: Int, event: KeyEvent?): Boolean {
        // Check if the key event was the Back button and if there's history
        val myWebView: WebView = findViewById(R.id.main_webview)
        if (keyCode == KeyEvent.KEYCODE_BACK && myWebView.canGoBack()) {
            myWebView.goBack()
            return true
        }
        // If it wasn't the Back key or there's no web page history, bubble up to the default
        // system behavior (probably exit the activity)
        return super.onKeyDown(keyCode, event)
```


## Reference
- https://developer.android.com/guide/webapps/webview#kotlin

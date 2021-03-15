#
### ■ DoubleBufferd 속성
###### - 출처 : https://docs.microsoft.com/ko-kr/dotnet/desktop/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls?view=netframeworkdesktop-4.8
###### § 속성 내용
######   - 그래픽 깜빡임 현상 줄이기
######     -> 모든 그리기 작업을 그리기 화면 대신 메모리 버퍼에 먼저 렌더링하여 그리기 작업이 완료되면 메모리 버퍼가 연결된 그리기 화면에 복사
###### - 사용법 
         DoubleBufferd = true;
                  or
         SetStyle(ControlStyles.OptimizedDoubleBuffer, true);

#
### ■ FormWindowState 속성 
###### - 출처 : https://docs.microsoft.com/ko-kr/dotnet/api/system.windows.forms.formwindowstate?view=net-5.0
###### § 속성 내용
######   - 창크기 속성 (Minimized, Maximized, Normal)
###### - 사용법 
         this.WindowState = FormWindowState.Minimized;
         
#
### ■ readonly 참조
###### - 출처 : https://docs.microsoft.com/ko-kr/dotnet/csharp/language-reference/keywords/readonly?f1url=%3FappId%3DDev15IDEF1%26l%3DKO-KR%26k%3Dk(readonly_CSharpKeyword);k(TargetFrameworkMoniker-.NETFramework,Version%253Dv4.5.2);k(DevLang-csharp)%26rd%3Dtrue //https://storycompiler.tistory.com/216
###### § 참조 내용
######   - 변수를 상수로 만듬
######   - const와 달리 complie 시점에 값을 확정하지 않고 runtime 시점에 이르러 값을 확정할 수 있음
###### ※ 초기화 되는 경우
######   - 변수 선언
######   - 생성자 안에서 변수값을 바꾸는 경우
###### § 활용
######   - 경로, 고정 변수, 초기값
###### - 사용법 
          public readonly int y = 5;
###### ![image](https://user-images.githubusercontent.com/74608323/111095967-e25db700-8581-11eb-8108-d037ca0b01f7.png)

### CSharp 유용기능 

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
### ■ Screen 클래스 : 다중 모니터 감지 
###### - 출처 : https://afsdzvcx123.tistory.com/entry/C-%EC%9C%88%ED%8F%BC-C-%EB%8B%A4%EC%A4%91-%EB%AA%A8%EB%8B%88%ED%84%B0-%EA%B0%90%EC%A7%80-%EB%B0%8F-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-Screen
###### - 1번 모니터와 2번 모니터에 각각 다른 창을 동시에 띄우는 기능 가능
###### - 사용법 
         using System;
         using System.Collections.Generic;
         using System.ComponentModel;
         using System.Data;
         using System.Drawing;
         using System.Linq;
         using System.Text;
         using System.Threading.Tasks;
         using System.Windows.Forms;

         namespace Example_210309
         {
             public partial class Form1 : Form
             {
                 Form2 form2 = new Form2();
                 public Form1()
                 {
                     InitializeComponent();

                     this.Load += Form1_Load;
                 }

                 private void Form1_Load(object sender, EventArgs e)
                 {
                     this.WindowState = FormWindowState.Maximized;
                     ScreenDetect();
                 }


                 private void ScreenDetect()
                 {
                     Screen[] sc = Screen.AllScreens;

                     if(sc.Length>1)
                     {
                         Screen screen = (sc[0].WorkingArea.Contains(this.Location) ? sc[1] : sc[0]);

                         form2.Show();
                         form2.Location = screen.Bounds.Location;
                         form2.WindowState = FormWindowState.Maximized;
                     }
                 }

             }
         }
         

#
### ■ ComboBox Filter 기능
###### - 출처 : https://afsdzvcx123.tistory.com/entry/C-%EC%9C%88%ED%8F%BC-Textbox-%EC%9E%85%EB%A0%A5%EB%90%9C-%EB%AC%B8%EC%9E%90%EC%97%B4%EB%A1%9C-ComboBox-%EB%8D%B0%EC%9D%B4%ED%84%B0-Filter-%EA%B8%B0%EB%8A%A5-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0?category=784689
###### - 사용법 
         using System;
         using System.Collections.Generic;
         using System.ComponentModel;
         using System.Data;
         using System.Drawing;
         using System.Linq;
         using System.Text;
         using System.Threading.Tasks;
         using System.Windows.Forms;

         namespace Example_210309
         {
             public partial class Form1 : Form
             {
                 List<string> comboList = new List<string>();

                 public Form1()
                 {
                     InitializeComponent();

                     AddItems();

                     ComboListAdd();
                 }   

                 private void AddItems()
                 {
                     cb_ProductList.Items.Add("두리안");
                     cb_ProductList.Items.Add("바나나");
                     cb_ProductList.Items.Add("키위");
                     cb_ProductList.Items.Add("사과");
                     cb_ProductList.Items.Add("토마토");
                     cb_ProductList.Items.Add("망고");
                     cb_ProductList.Items.Add("애플망고");
                     cb_ProductList.Items.Add("포도");
                     cb_ProductList.Items.Add("거봉");
                     cb_ProductList.Items.Add("호두");
                 }

                 private void ComboListAdd()
                 {
                     for(int index = 0; index < cb_ProductList.Items.Count; index++)
                     {
                         comboList.Add(cb_ProductList.Items[index].ToString());
                     }
                 }


                 private void tb_Filter_TextChanged(object sender, EventArgs e)
                 {
                     this.Cursor = Cursors.WaitCursor;

                     cb_ProductList.Items.Clear();
                     ComboListAdd();

                     string filterString = tb_Filter.Text.ToString();

                     var result = comboList.Where(x => x.Contains(filterString)).ToArray();

                     cb_ProductList.Items.AddRange(result);

                     this.Cursor = Cursors.Default;

                 }
             }
         }

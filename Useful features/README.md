# C# DataGridView 사용 팁
#### 출처 : https://najsulman.tistory.com/460
#### 1) 홀수 행 다른 색상으로 표현
###### ![image](https://user-images.githubusercontent.com/74608323/110408852-9adeb300-80c9-11eb-99f3-482c53ade236.png)
###### - 사용법
         dbGridView.AlternatingRowsDefaultCellStyle.BackColor = Color.Aqua;
         
#
#### 2) 행단위로 선택
###### ![image](https://user-images.githubusercontent.com/74608323/110409195-40922200-80ca-11eb-93a8-17b33f516b1e.png)
###### - 사용법
         dbGridView.SelectionMode = DataGridViewSelectionMode.FullRowSelect;
         
#
#### 3) 행 인덱스 표시
###### - 사용법 : RowPostPaint ( 셀 생성 후 행을 화면에 보여줄떄 발생하는 이벤트 )
         private void dbGridView_RowPostPaint(object sender, DataGridViewRowPostPaintEventArgs e)
         {
            Rectangle rect = new Rectangle(e.RowBounds.Location.X, e.RowBounds.Location.Y, 
            dbGridView.RowHeadersWidth - 4, e.RowBounds.Height);

            TextRenderer.DrawText(e.Graphics,(e.RowIndex+1).ToString(),
            dbGridView.RowHeadersDefaultCellStyle.Font,rect,dbGridView.RowHeadersDefaultCellStyle.ForeColor,
            TextFormatFlags.VerticalCenter|TextFormatFlags.Right);
         }
###### - 주의 사항 : 첫 열을 만들어 주지 않은 상태에서 함수 적용시 기존 0열 데이터와 인덱스정보가 같이 표시됨

#
#### 4) GridView 실행시 기본열 선택안되게 하기

###### ![image](https://user-images.githubusercontent.com/74608323/110412641-de3c2000-80cf-11eb-8070-a5e03c307aea.png)
###### - 사용법 : Form Event Shown -> Grid 속성 값 CurrentCell = null 적용 
        private void Form_Shown(object sender, EventArgs e)
        {
            dbGridView.CurrentCell = null;
        }
        
#
#### 5) 특정 행이나 열 고정 기능 (엑셀 틀 고정 기능)
###### ![image](https://user-images.githubusercontent.com/74608323/110421304-8fe34d00-80e0-11eb-8e61-1b3f67dbb213.png)
###### - 사용법 : Frozen 속성 활용
         dbGridView.Columns[1].Frozen = true;

#
#### 6) 특정 행이나 열 고정 기능 (엑셀 틀 고정 기능)
###### - 사용법 : Frozen 속성 활용
         private void grdMotorSpd_EditingControlShowing(object sender, DataGridViewEditingControlShowingEventArgs e)
         {
            TextBox tb = e.Control as TextBox;

            if(tb == null)
            {
                return;            
            }
            if(grdMotorSpd.CurrentCell.ColumnIndex == 1)
            {
                tb.AutoCompleteMode = AutoCompleteMode.SuggestAppend;
                tb.AutoCompleteSource = AutoCompleteSource.AllSystemSources;
            }
            else
            {
                tb.AutoCompleteMode = AutoCompleteMode.None;
            }
        }
###### § 참고사이트
######  - https://m.blog.naver.com/PostView.nhn?blogId=gg2ee44&logNo=90023304981&proxyReferer=https:%2F%2Fwww.google.com%2F
######  - http://ngmsoftware.com/bbs/board.php?bo_table=study&wr_id=140

#
#### 7) 열 순서 바꾸기 ( 사용자가 원하는 순서대로 배치할 떄 유용한 기능)
###### ![image](https://user-images.githubusercontent.com/74608323/110426017-b1483700-80e8-11eb-80b9-306caf1cc159.png)
###### - 사용법 : AllowUserToOrderColumns 속성 활용
         dbGridView.AllowUserToOrderColumns = true;        
###### ![image](https://user-images.githubusercontent.com/74608323/110426136-e6548980-80e8-11eb-8afd-faaf58c73ead.png)


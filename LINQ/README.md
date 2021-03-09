### CSharp-LINQ

### ■ 기본 사용 방법 (using System.Linq;)
###### - 출처 : https://hijuworld.tistory.com/56
###### - from, where, order by, select등을 활용하여 데이터 추출
###### - 사용법 
###### ex) 2의 배수 추출
        using System;
        using System.Linq;
        using System.Windows.Forms;

        namespace Example_210309
        {
            public partial class Form1 : Form
            {
                int[] nums = new int[9] { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
                public Form1()
                {
                    InitializeComponent();           
                }

                private void button1_Click(object sender, EventArgs e)
                {
                    var result = from num in nums           // 변수 nums의 값을 변수 num에 대입
                                 where (num % 2) == 0       // 2의 배수인 값 찾기
                                 select num;                // num을 추출하여 result에 저장
                    foreach (int num in result)
                    {
                        tb_Result.AppendText(num + " ");
                    }

                }
            }
        }
###### ![image](https://user-images.githubusercontent.com/74608323/110446127-2bd18080-8102-11eb-8470-58901fec1342.png)


###### ex) 60점 이상인 사람 이름순으로 추출
        using System;
        using System.Collections.Generic;
        using System.Linq;
        using System.Windows.Forms;

        namespace Example_210309
        {
            public class Student
            {
                public string name { get; set;}
                public int score { get; set; }
            }

            public partial class Form1 : Form
            {
                List<Student> students;

                public Form1()
                {
                    InitializeComponent();
                    AddStudent();
                }

                private void AddStudent()
                {
                    //using System.Collections.Generic;
                    students = new List<Student>
                    {
                        new Student{name ="x1",score = 80},
                        new Student{name ="x2",score = 40},
                        new Student{name ="x3",score = 73},
                        new Student{name ="x4",score = 69},
                        new Student{name ="x5",score = 37},
                        new Student{name ="x6",score = 68},
                        new Student{name ="x7",score = 73}
                    };
                }


                private void button1_Click(object sender, EventArgs e)
                {
                    var result = from student in students           
                                 where student.score  >= 60       // 성적 60점이상만
                                 orderby student.name ascending   //이름순으로 정렬 ascending : 오름차순 descending : 내림차순
                                 select student.name;             //이름만 추출
                    foreach (string name in result)
                    {
                        tb_Result.AppendText(name + " ");
                    }

                }
            }
        }
######  ![image](https://user-images.githubusercontent.com/74608323/110446043-19efdd80-8102-11eb-99d7-40d9a4d6f294.png)
        
        
### ■ 집계함수 방법 (using System.Linq;)
###### - 출처 : https://hijuworld.tistory.com/57?category=817153
###### - Sum(합), Max(최댓값), Min(최솟값), count(데이터개수), Average(평균값), Aggregate( 활용하여 데이터 추출
###### - 사용법 
        using System;
        using System.Linq;
        using System.Windows.Forms;

        namespace Example_210309
        {
            public partial class Form1 : Form
            {
                int[] nums = new int[5] { 1, 2, 3, 4, 5};
                public Form1()
                {
                    InitializeComponent();
                }

                private void button1_Click(object sender, EventArgs e)
                {
                    string[] result = new string[7];
                    result[0] = "sum : " + nums.Sum().ToString();
                    result[1] = "max : " + nums.Max().ToString();
                    result[2] = "min : " + nums.Min().ToString();
                    result[3] = "average : " + nums.Average().ToString();
                    result[4] = "count : " + nums.Count().ToString();
                    //Aggregate 사용자가 직접 데이터의 가공 방식을 명시할 수 있다.
                    var data = nums.Aggregate((num1, num2) => num1 * num2);
                    result[5] = data.ToString();
                    data = nums.Aggregate(100,(num1, num2) => num1 * num2);
                    result[6] = data.ToString();

                    list_Result.Items.AddRange(result);

                }
            }
        }
  ###### ![image](https://user-images.githubusercontent.com/74608323/110446331-64715a00-8102-11eb-81f9-bd9f5a86dd04.png)  
      
  ### ■ 응용 (using System.Linq;)
  ###### ex) 50점 이상, 50점 미만 학생수, 최대값, 평균값 추출하기

        using System;
        using System.Collections.Generic;
        using System.Linq;
        using System.Windows.Forms;

        namespace Example_210309
        {
            public class Student
            {
                public string name { get; set; }
                public int score { get; set; }
            }

            public partial class Form1 : Form
            {
                List<Student> students;

                public Form1()
                {
                    InitializeComponent();
                    AddStudent();
                }

                private void AddStudent()
                {
                    //using System.Collections.Generic;
                    students = new List<Student>
                        {
                            new Student{name ="x1",score = 80},
                            new Student{name ="x2",score = 40},
                            new Student{name ="x3",score = 73},
                            new Student{name ="x4",score = 69},
                            new Student{name ="x5",score = 37},
                            new Student{name ="x6",score = 68},
                            new Student{name ="x7",score = 73}
                        };
                }


                private void button1_Click(object sender, EventArgs e)
                {
                    var result = from student in students
                                 group student by student.score >= 50 into g
                                 select new
                                 {
                                     key = g.Key == true ? "50점이상" : "50점미만",
                                     count = g.Count(),
                                     avr = g.Average(student => student.score),
                                     max = g.Max(student => student.score)
                                 };
                    foreach (var data in result)
                    {
                        list_Result.Items.Add(data.key + " 학생 수 :" + data.count);
                        list_Result.Items.Add(data.key + " 중 최대점수 :" + data.max);
                        list_Result.Items.Add(data.key + " 학생들의 평균 :" + data.avr);
                        list_Result.Items.Add("----------------------------------------");

                    }

                }
            }
        }
  ######   ![image](https://user-images.githubusercontent.com/74608323/110446275-54f21100-8102-11eb-9871-1a10a5f22a6a.png)



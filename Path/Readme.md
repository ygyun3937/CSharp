### Path Method
##### 출처
##### 1.https://docs.microsoft.com/ko-kr/dotnet/api/system.io.path?view=netframework-4.8
##### 2.https://sinb57.tistory.com/entry/Path-%ED%81%B4%EB%9E%98%EC%8A%A4-%EC%82%B4%ED%8E%B4%EB%B3%B4%EA%B8%B0?category=799078
#
##### 1. 지정된 경로 확장자명 없이 파일이름만 반환
#####   - 함수명 : GetFileNameWithoutExtension
#####   - 사용법 
          String path1 = @"C:\Users\USER\Desktop\hello.exe";
          String path2 = @"C:\Users\USER\Desktop\";

          String fileName1 = Path.GetFileName(path1); // hello.exe 반환
          String fileName2 = Path.GetFileNameWithoutExtension(path1); // hello 반환
#
##### 2. 지정된 경로 확장자 반환
#####   - 함수명 : GetExtension
#####   - 사용법 
          String path1 = @"C:\Users\USER\Desktop\hello.exe";

          String fileName1 = Path.GetExtension(path1); // .exe 반환
#
##### 3. 확장자명 변경
#####   - 함수명 : ChangeExtension
#####   - 사용법 
          String path1 = @"C:\Users\USER\Desktop\hello.exe";
          String temp1, temp2, temp3 = "";

          temp1 = Path.ChangeExtension(path1, ".doc");      // C:\Users\USER\Desktop\hello.doc
          temp2 = Path.ChangeExtension(path1, "doc");       // C:\Users\USER\Desktop\hello.doc
          temp3 = Path.ChangeExtension(path1, "");          // C:\Users\USER\Desktop\hello.         
#
##### 4. 경로 내에 확장자 포함 여부 확인
#####   - 함수명 : HasExtension
#####   - 사용법 
            String path1 = @"C:\Users\USER\Desktop\hello.exe";
            String path2 = @"C:\Users\USER\Desktop\hello";
            String path3 = @"C:\Users\USER\Desktop\";

            bool bresult = false;

            bresult = Path.HasExtension(path1);
            Console.WriteLine(bresult);                     //True

            bresult = Path.HasExtension(path2);
            Console.WriteLine(bresult);                     //False

            bresult = Path.HasExtension(path3);
            Console.WriteLine(bresult);                     //False
            
            
            

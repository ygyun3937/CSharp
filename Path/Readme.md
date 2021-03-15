### Path Method
#
##### 1. 절대 경로 반환
#####   - 함수명 : GetFullPath
#####   - 사용법 
          String path1 = @"C:\Users\USER\Desktop\hello.exe";
          String path2 = @"C:\Users\USER\Desktop\";

          String fileName1 = Path.GetFileName(path1); // hello.exe 반환
          String fileName2 = Path.GetFileNameWithoutExtension(path1); // hello 반환

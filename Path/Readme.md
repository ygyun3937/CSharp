### Path Method
#
##### 1. 지정된 경로 확장자명 없이 파일이름만 반환
#####   - 함수명 : GetFullPath
#####   - 사용법 
          String path1 = @"C:\Users\USER\Desktop\hello.exe";
          String path2 = @"C:\Users\USER\Desktop\";

          String fileName1 = Path.GetFileName(path1); // hello.exe 반환
          String fileName2 = Path.GetFileNameWithoutExtension(path1); // hello 반환
#
##### 2. 지정된 경로 확장자 반환
#####   - 함수명 : GetFullPath
#####   - 사용법 
          String path1 = @"C:\Users\USER\Desktop\hello.exe";

          String fileName1 = Path.GetExtension(path1); // .exe 반환

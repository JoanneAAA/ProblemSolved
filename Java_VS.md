# Visio Studio Probs Record 1. 無法編譯，error報亂碼[Java]
這可能不只出現在編譯 Java 語言時，當已經檢查無數次確定程式沒有問題但 debug 不過並且出現亂碼時，你可能遇到編碼問題

環境：Windows10

以下是在彭彭java教學影片中的部分code，是此次發生編譯問題的目標對象
```
//void代表方法沒有回傳值，方法中使用return直接中斷
class Test {
    public static void main(String[] args){
        //程式進入點，若無任何動作會無法執行定義的方法
        Test.talk("Hello");//呼叫類別的方法
        Test.talk("你好");
        //因為不同的輸入(content)達到更高的彈性
        int ans = BasicMath.add(3, 5);
        System.out.println(ans);
        BasicMath.multiply(4, 7);
    }
    //定義更多自己的類別方法
    static void talk(String content){
        System.out.println(content);

    }
    
}
class BasicMath{
    static int add(int n1, int n2){
        int result = n1+n2;
        return result;
    }
    static int multiply(int n1, int n2){
        int result = n1*n2;
        return result;
    }
}

```
當進行編譯時，在 VS 右下角雖顯示編碼是使用UTF-8，但 terminal 窗口顯示亂碼，這時很明顯是編碼讀取時出的問題
![image](https://github.com/user-attachments/assets/e0dac9b5-7b7a-4084-8f6b-ed333bc88920)
在這次情況中可以在 terminal 中檢查 Java 環境的預設編碼，輸入 chcp 後 terminal 回傳950，這代表Windows預設使用 Big5 (x-windows-950)，而Java預設使用 UTF-8，所以需要手動指定 -encoding UTF-8 來編譯程式。

![image](https://github.com/user-attachments/assets/bfcd456f-9fbe-4241-aa81-852593fea920)
強制使用UTF-8編碼， terminal 輸入```javac -encoding UTF-8 [檔案名稱].java```，此處是使用 App2.java 檔案，輸入後即可正確編譯
![image](https://github.com/user-attachments/assets/f2095e4e-ec35-4421-8532-8e4be263eaec)

## 其他無法編譯的可能原因
除了terminal亂碼以外，無法編譯java檔也會有寫在檔案中的class不會出現在指定資料夾中的情形，VS 中 Explorer 應正常顯示 Java 檔案以及對應的 class，當不確定 Java 檔是否被正確編譯，可以在 terminal 中輸入```java [class名稱]```，當 terminal 報找不到時可以先確認：

1. 是否已經編譯過 Java 檔案，當更新檔案影響到 class 後請不要忘記重新在 terminal 輸入```javac [檔案名稱].java```
2. 確認你在正確的資料夾，用 ls 或 dir 指令（視你的系統而定）檢查你的 .java 和 .class 是否存在：
```
ls   # Mac/Linux
dir  # Windows
```
應該要看到 .java和所有的 .class，若沒有必須回到正確的資料夾

3. 當發生 javac 無法使用時請在 terminal 輸入：
```
java -version
javac -version
```
若出現 command not found，請先安裝 JDK，另外也可以利用 VS 中的套件功能加裝擴充工具，例如：Language Support for Java(TM) by Red Hat、JavaFX Support、Extension Pack for Java、Test Runner for Java、Project Manager for Java、Debugger for Java等。

--02/23/2025，Joanne的學習筆記

contact: [JoanneChangkwea@gmail.com](mailto:joannechangkwea@gmail.com)


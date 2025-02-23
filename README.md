# Visio Studio java compiling problems record
This is a simple question yet may drive ppl like me crazy when your code doesn't work out in Visio Studio...
//void代表方法沒有回傳值，方法中使用return直接中斷
class Test {
    public static void main(String[] args){
        //程式進入點，若無任何動作會無法執行定義的方法
        Test.talk("Hello");//呼叫類別的方法
        Test.talk("你好");
        //因為不同的輸入(content)達到更高的彈性
        int ans = BasicMath.add(3, 5);
        System.out.println(ans);
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
        //System.out.println(result);
        return result;
    }
    static int multiply(int n1, int n2){
        int result = n1*n2;
        return result;
    }
}

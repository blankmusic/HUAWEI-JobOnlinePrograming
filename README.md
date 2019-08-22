## HUAWEI-JobOnlinePrograming
# 第一题报文转义
0x0A-->0x12 0x34<br>
0X0B-->0xAB 0xCD<br>
其他报文字节保持不变
# 输入描述
输入报文为16进制，报文长度不超过129，输入报文的第一个字节为报文长度，第一个字节算正式报文的一部分，但不参与转义<br>
输入报文每个字节用空格隔开<br>
# 输出描述
输出报文的第一个字节算是真正报文的一部分，为准以后的报文长度<br>
输出报文的内容都为大写的16进制，前不带0x前缀<br>
输出报文每个字节用空格隔开<br>

# 题解

```java
import java.util.ArrayList;
import java.util.Scanner;

public class Main {
  public static void main(String[] args){
      Scanner s=new Scanner(System.in);
      String[] str=s.nextLine().split(" ");
      int count=Integer.parseInt(str[0],16);
      ArrayList<String> ret=new ArrayList<>();
      for(int i=1;i<count;i++){
          if(str[i].charAt(i)=='A'||str[i].charAt(i)=='a'){
              ret.add("12");
              ret.add("34");
          }else if(str[i].charAt(i)=='B'||str[i].charAt(i)=='b'){
              ret.add("AB");
              ret.add("CD");
          }else {
              ret.add(str[i]);
          }
      }
      for(String r:ret){
      System.out.print(r+" ");
      }

  }

}

```

#  第二题 质数
  # 输入描述
  输入Low 和High ，Low>High<br>
  # 输出描述
  输出 minIndx 为low到high中所有质数的十位之和与个位之和中较小的那个。
  
  # 题解
  ```java
  import java.util.Scanner;

public class Main {
  public static void main(String[] args){
      Scanner s=new Scanner(System.in);
      int l=s.nextInt();
      int h=s.nextInt();
      int t1=0;
      int t2=0;
      for(int i=l;i<h;i++){
          boolean b=true;
          for(int t=2;t<i;t++) {
              if (i % t == 0) {
                  b = false;
              }
          }
          if(b) {
               t1+=i % 10;//个位和
               t2+=i / 10 % 10;//十位和
          }
      }
      System.out.println(Math.min(t1,t2));
  
      
  }

}
  
  ```
  
 # 第三题 群组消息数目
 # 题目描述
 A有一条消息，转发到群里，群里的人再转发到别的群里。输出所有看到这条消息的人数。
 # 输入示例
 a
 转发消息<br>
 群1成员:a,b ,c,d,e<br>
 群2成员:b,c,f<br>
 群3成员: a,d,g<br>
 
 # 题解
(牛客网)https://uploadfiles.nowcoder.com/images/20190821/9227537_1566394486724_EEEE11D0AD54E4DA2217344CD2846D22

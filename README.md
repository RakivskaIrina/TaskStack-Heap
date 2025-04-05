# TaskStack-Heap
solution task - Stack-Heap diagram

Вихідний код:
public class Main {
    public static void main(String[] args) {
        String name = "Kevin";
        List<String> list = new ArrayList<>();
        int times = 10;
        System.out.println(times + fill(list, name + name, times));
    }
    public static int fill(Collection<String> collection, String str, int times){
        String shrunk = shrink(str);
        times = (times + shrunk.length()) / 2;
        for (int i = 0; i < times / 2; i++) {
            collection.add(shrunk);
        }
        return times;
    }
 
    public static String shrink(String str){
        int newLength = str.length() / 2 + str.length() % 2;
        char[] chars = new char[newLength];
        for (int i = 0; i < str.length(); i+=2) {
            chars[i / 2] = str.charAt(i);
        }
        return new String(chars);
    }
}


Стек використовується для зберігання локальних змінних примітивних типів та посилань на об'єкти.
у методi main():
-times —  int, тому значення буде записане в стек;
- name — посилання на об'єкт типу String. У стеку буде збережено посилання, а сам об'єкт "Kevin" — в String Pool, який є частиною Heap;
- list — посилання на об'єкт ArrayList, сам об'єкт створюється через new, отже, міститься в купі, а посилання зберігається в стеку.

у методi fill():
- str - посилання на "KevinKevin" (в Heap)
- times - int, тому значення буде записане в стек;
при виклику shrink(str):
- на вершині стеку створюється новий фрейм для методу shrink
У цьому новому фреймі створюється:
- змінна newLength, обчислена як str.length() / 2 + str.length() % 2 = 5
- масив char[] chars, який створюється в купі, але посилання на нього зберігається в стеку методу shrink.

Потім метод заповнює масив символами з парних позицій, результат — масив {'K','v','n','v','n'}.

масив передається в new String(chars), створюється новий об'єкт рядка "Kvnvn" у купі, і його посилання повертається назад у метод fill().

![1](https://github.com/user-attachments/assets/71678bbd-efd1-405b-8af4-82dcee488bf4)



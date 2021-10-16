## Задача 1. Межпоточный диалог

### Описание
Так как мы уже научились работать с потоками, сейчас нам необходимо создать несколько потоков (3-4 потока), 
которые каждые 2-3 секунды отправляют в консоль некоторое сообщение, обязательно содержащее имя потока, которое 
было задано при создании. Поток должен выполнять бесконечный цикл вывода сообщения и сна (задержки). Главный поток 
программы (метод main) должен дать поработать остальным потокам какое-то время (секунд 15), а потом одним методом 
завершить все созданные ранее потоки.

### Функционал программы
1. Создание 4 потоков, каждый из которых имеет свое имя.
2. Каждые 2-3 секунды поток печатает сообщение в консоль. Обязательно в сообщении должно фигурировать имя потока
3. Через какое-то время (например 15 секунд), главный поток должен одним методом завершить все созданные ранее потоки

### Пример
Пример 1
```
Создаю потоки...
Я поток 1. Всем привет!
Я поток 2. Всем привет!
Я поток 4. Всем привет!
Я поток 3. Всем привет!
Я поток 2. Всем привет!
Я поток 1. Всем привет!
Я поток 3. Всем привет!
Я поток 4. Всем привет!
Я поток 4. Всем привет!
Я поток 3. Всем привет!
Я поток 2. Всем привет!
Я поток 1. Всем привет!
Завершаю все потоки.
```

## Реализация
1. Напишите свой собственный класс-поток `MyThread` или иное название, который переопределит метод run таким образом, чтобы раз в несколько секунд печатать сообщение в консоль.

```java
class MyThread extends Thread {

    @Override
    public void run() {
      try {
        while(!isInterrupted()) {
          Thread.sleep(2500);
          System.out.println("Всем привет!");
        }
      } catch (InterruptedException err) {
        
      } finally{
        System.out.printf("%s завершен\n", getName());
      }
    }
}
```

2. Допишите в вывод сообщения имя потока. Оно не должно быть "хардкоженным", нужно использовать методы класса `Thread`
3. Создайте 4 экземпляра созданного класса и запустите их.
4. Усыпите поток на некоторое время (15 секунд)
5. Завершите все ранее созданные потоки, вызвав один метод. Обратитесь к лекции, если испытываете затруднения с реализацией.



<details>
  <summary>Подсказка</summary>
  
  Используйте метод `Thread.getCurrentThread.getName()` для получения имени текущего потока. Используйте `Thread` для создания потоков, не используйте пулы. Используйте `ThreadGroup` для группировки процессов и управления ими как одним
</details>



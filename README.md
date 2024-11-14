# Lab2
## Отчет по лабораторной работе № 2

#### № группы: `ПМ-2401`

#### Выполнила: `Ершова Алина Дмитриевна`

#### Вариант: `13`

### Cодержание:

- [Постановка задачи](#1-постановка-задачи)
- [Входные и выходные данные](#2-входные-и-выходные-данные)
- [Математическая модель](#2.5-математическая-модель)
- [Выбор структуры данных](#3-выбор-структуры-данных)
- [Алгоритм](#4-алгоритм)
- [Программа](#5-программа)
- [Анализ правильности решения](#6-анализ-правильности-решения)

### 1. Постановка задачи 

>Напишите программу на Java, которая выполняет следующие действия с трёхмерным массивом дробных чисел: 
>>1. Считывает с консоли размеры массива X, Y и Z, затем элементы 
массива размером X × Y × Z. 
>>2. В каждом столбце (фиксируя координаты Y и Z) сортирует элементы по убыванию их дробной части. Если дробные части равны, сортирует по возрастанию целой части. 
>>3. Находит и выводит среднее геометрическое элементов каждого слоя (по координатам X и Y ). 
>>4. Выводит элементы массива - (x, y, z : значение). 
>>5. Округляет все элементы массива до двух знаков после запятой и выводит обновлённый массив 


Представим трёхмерный массив в виде параллелепипеда. `X` - кол-во столбцов, `Y` - кол-во строк, `Z` - кол-во слоёв.

Разобью задачу на подзадачи

1.Сортируем элементы по убыванию дробной части (если дробные части равны, сортируем по целой части) в каждом столбце трёхмерного массива. (фиксируем `Х` и меняем `Y`  и  `Z`).

2.Фиксируя `Z`, перемножаем элементы каждого слоя, извлекаем корень степени `X` * `Y`  (т.к. элементов на одном слое `X` * `Y` шт.)  и таким образом находим сред. геом. выводим его.

3.Затем выводим массив в виде `x`, `y`, `z` : значение.

4.Каждый элемент массива округляем до двух знаков после запятой и выводим новый массив.


### 2. Входные и выходные данные.

#### Данные на вход

На вход сначала подаются 3 натуральных числа `X`, `Y` и `Z` (натуральные т.к. это размер массива).

Затем, по условию, подаются `X` * `Y` * `Z` дробных чисел.

|             | Тип                | min значение    | max значение   |
|-------------|--------------------|-----------------|----------------|
|X (Число 1)|	Натуральное число|	1           |	2<sup>31</sup>-1|
| Y (Число 2)|	Натуральное число|	1           |	2<sup>31</sup>-1|
| Z (Число 3)|	Натуральное число|	1           |	2<sup>31</sup>-1|
| N_0 (Число 4) | Вещественное число |-1.79<sup>308</sup>|1.79<sup>308</sup>|
| N_1 (Число 5) | Вещественное число |-1.79<sup>308</sup>|1.79<sup>308</sup>|
| ... | ... |...|...|
| N_`X` * `Y` * `Z` (Число `X` * `Y` * `Z` - 3) | Вещественное число |-1.79<sup>308</sup>|1.79<sup>308</sup>|


#### Данные на выход

Программа будет выводить `Z` вещ. чисел - среднее геометрическое.

Затем будет выведено `X` * `Y` * `Z` элементов массива вещественного типа. Вида `x` , `y` , `z` : значение

После будет выведено еще `X` * `Y` * `Z` вещ. чисел обновлённого массива.


|             | Тип                | min значение    | max значение   |
|-------------|--------------------|-----------------|----------------|
| Cреднее геометрическое                                            |
| Число 1 | Вещественное число |-1.79<sup>308</sup>|1.79<sup>308</sup>|
| ... | ... |...|...|
| Число Z | Вещественное число |-1.79<sup>308</sup>|1.79<sup>308</sup>|
| Mассив                                                            |
| Число 1 | Вещественное число |-1.79<sup>308</sup>|1.79<sup>308</sup>|
| ... | ... |...|...|
| Число `X` * `Y` * `Z`  | Вещественное число |-1.79<sup>308</sup>|1.79<sup>308</sup>|
| Обновлённый массив                                                |
| Число1 | Вещественное число |-1.79<sup>308</sup>|1.79<sup>308</sup>|
| ... | ... |...|...|
| Число `X` * `Y` * `Z` | Вещественное число |-1.79<sup>308</sup>|1.79<sup>308</sup>|



### 2.5. Математическая модель

Формула среднего геометрического - (x<sub> 1 </sub> * x<sub> 2 </sub> * ... * x<sub> n </sub> )<sup> 1/n </sup>

### 3. Выбор структуры данных.

Программа ролучает 3 натуральных числa `X` , `Y` и `Z`.  Минимальное значение натурального числа это 1, а максимальное не ограниченно(в java максимальное - 2<sup>31-1</sup>) тип int.

Затем программа получает `X` * `Y` * `Z` дробных чисел - элементы массива a, будет создан массив типа `double` и размером `X` * `Y` * `Z`.

В коде программы будут также использоваться переменные с типом данных `double`: 

peremem - вспомогательная переменая для сортировки элелементом (подзадача 1)

product - переменная, в которую будет записываться произведение элементова (подзадача 2)

Также для подзадачи 1 будет создан массив `m` размера `х`, в который будут записываться отсортированные числа. Тип данных - `double`.             

|             | название переменной | Тип (в Java) | 
|-------------|---------------------|--------------|
| X (Число 1) | `x`                 | `int`     |
| Y (Число 2) | `y`                 | `int`     | 
| Z (Число 3) | `z`                 | `int`     |
| a_0 (Число 4) | `a[0][0][0]`                 | `double`     |
| a_1 (Число 5) | `a[0][0][1]`                 | `double`     |
| ... | ...                 | ...     | 
| a_`X` * `Y` * `Z` -  1 (Число `X` * `Y` * `Z` - 3) | `a[z][x][y]`                 | `double`     |
| Переменные в коде программы     | 
|  peremen | `peremen`                 | `double`     |
| product | `product`                 | `double`     |
|m_0 | `m[0]` |  `double`|
|m_1 | `m[0]` |  `double`|
| ... | ... |  ... |
|m_x-1 | `m[x-1]` |  `double`|

Для вывода можно не создавать отдельные переменные.

### 4. Алгоритм

1. Ввод данных 

Вводим натурал. Числа `X` ,  `Y` и `Z`.

2. Создание и заполнение массива.
   
Создаем трехмерный массив `а` с типом данных `double`.

В него записываем введенные с клавиатуры дробныe числa.

3. Выполнение подзадач
   
3.1 Затем создаю массив `м`, в который записываем элемент 0-го столбца, сотритируем его по дробной части, если дробные части равны,сортируем по целой части и т.д. для оставшихся столбцов. Значения массива `м` приписываем массиву `а`. (Обновляем массив `а`, согласно условию сортировки)

3.2 Затем нахожу произведение чисел находящихся на 0-ом слое. И вычисляю корень степени (`х` * `у` ) из получившегося произведения. И вывожy результат. И т.д. для отставшихся слоёв.

3.3 После вывожу массив в виде `x` , `y` , `z` : значение

3.4 И, наконец, перебором элеметнов, попутно округляя до двух знаков после запятой, вывожу обновлённый массив.

### 5. Программа

```java
import java.io.PrintStream;
import java.util.Scanner;
public class Main {
    public static Scanner in = new Scanner(System.in);
    public static PrintStream out = System.out;

    public static void main(String[] args) {
        int x = in.nextInt();
        int y = in.nextInt();
        int z = in.nextInt();
        double[][][] a = new double[z][x][y];
        //создание массива из введенных элементов
        for (int i = 0; i < z; i++) {
            for (int j = 0; j < x; j++) {
                for (int k = 0; k < y; k++) {
                    a[i][j][k] = in.nextDouble();
                }
            }
        }
        //сортировка по Х
        for (int i = 0; i < z; i++) {
            for (int j = 0; j < y; j++) {
                double[] m = new double[x]; //создание вспомогательного массива м
                for (int k = 0; k < x; k++) {
                    m[k] = a[i][k][j];
                }
                //здесь у нас новый массив м (столбец х). Отсортируем его и вставим вместо столбца в массив а
                for (int p = 0; p < x; p++) {
                    for (int p1 = p + 1; p1 < x; p1++) {
                        double peremen = 0; //вспомогательная переменная для перезаписи элементов массива
                        if ((m[p] - (int) m[p]) < (m[p1] - (int) m[p1])) { //сравнение дробных частей чисел
                            peremen = m[p];
                            m[p] = m[p1];
                            m[p1] = peremen;
                        }
                        else {
                            if ((m[p] - (int) m[p]) == (m[p1] - (int) m[p1])) {//если дробные части равны...
                                if (((int) m[p]) > ((int) m[p1])) { //сортируем по целой части
                                    peremen = m[p];
                                    m[p] = m[p1];
                                    m[p1] = peremen;
                                }
                            }
                        }
                    }
                }
                //здесь у нас отсортированный массив м
                for (int k = 0; k < x; k++) { //"обновляем" стоблец массива а
                    a[i][k][j] = m[k];
                }
            }
        }
        out.println("Среднее геом.:");
        for (int i = 0; i<z; i++) {
            double product = 1;
            for (int j = 0; j < x; j++) {
                for (int k = 0; k < y; k++) {
                    product *= a[i][j][k]; //находим произведение всех элементов слоя
                }
            }
            out.println(Math.pow(product, ((double)1/(x*y)))); //выводим сред. геом.
        }

        out.println("Вывод массива в виде x, y, z: значение");
        for (int i = 0; i<z; i++) {
            for (int j = 0; j < x; j++) {
                for (int k = 0; k < y; k++) {
                    out.println(j+", "+k+", "+i+": "+a[i][j][k]);
                }
            }
        }
        out.println("массив с округленными эл.:");
        for (int i = 0; i<z; i++) {
            for (int j = 0; j < x; j++) {
                for (int k = 0; k < y; k++) {
                    a[i][j][k] = Math.round(a[i][j][k] * 100.0) / 100.0; //округляю эл. до 2-х знаков после запятой
                    out.print(a[i][j][k]+" "); //вывожу массив с округленными элементами
                }
                out.println();
            }
            out.println("===");
        }
    }
}
```

### 6. Анализ правильности решения

1. Тест для массива 1 * 1 * 1
    - **Input**:
        ```
        1 1 1
        
        5,678
        ```

    - **Output**:
        ```
        Среднее геом.:
        5.678
        
        Вывод массива в виде x, y, z: значение
        0, 0, 0: 5.678
        
        Массив с округленными эл.:
        5.68 
        ```
2. Тест для массива 2 * 2 * 2
    - **Input**:
        ```
        2 2 2

        4,876 675,6 34,6566 55,98 56,78 34,4763 54,78 9,758539
        ```

    - **Output**:
        ```
         Среднее геом.:
         50.2797
         31.9838
        
         Вывод массива в виде x, y, z: значение
         0, 0, 0: 4.876
         0, 1, 0: 55.98
         1, 0, 0: 34.6566
         1, 1, 0: 675.6
         0, 0, 1: 54.78
         0, 1, 1: 9.758539
         1, 0, 1: 56.78
         1, 1, 1: 34.4763
        
         Массив с округленными эл.:
         4.88 55.98 
         34.66 675.6 
         ===
         54.78 9.76 
         56.78 34.48
        ```

4. Тест для массива 3 * 3 * 3
    - **Input**:
        ```
         3 3 3
        
         24,450 56,63 89 34,560 51,630 55 45,576 84 93,5734 264,43 57,3 85 4,999 51,6301 5 45,530 84 9,54 24,455 63 89,745 34,5654 51,63 59 45,501 4 94 
        ```

    - **Output**:
        ```
         Среднее геом.:
         54,6278
         33,9953
         51,3874
         
         Вывод массива в виде x, y, z: значение
         0, 0, 0: 45.576
         0, 1, 0: 51.63
         0, 2, 0: 93.5734
         1, 0, 0: 34.56
         1, 1, 0: 56.63
         1, 2, 0: 55.0
         2, 0, 0: 24.45
         2, 1, 0: 84.0
         2, 2, 0: 89.0
         0, 0, 1: 4.999
         0, 1, 1: 51.6301
         0, 2, 1: 9.54
         1, 0, 1: 45.53
         1, 1, 1: 57.3
         1, 2, 1: 5.0
         2, 0, 1: 264.43
         2, 1, 1: 84.0
         2, 2, 1: 85.0
         0, 0, 2: 34.5654
         0, 1, 2: 51.63
         0, 2, 2: 89.745
         1, 0, 2: 45.501
         1, 1, 2: 4.0
         1, 2, 2: 59.0
         2, 0, 2: 24.455
         2, 1, 2: 63.0
         2, 2, 2: 943.0
         
         Массив с округленными эл.:
         45.58 51.63 93.57 
         34.56 56.63 55.0 
         24.45 84.0 89.0 
         ===
         5.0 51.63 9.54 
         45.53 57.3 5.0 
         264.43 84.0 85.0 
         ===
         34.57 51.63 89.75 
         45.5 4.0 59.0 
         24.46 63.0 943.0        
        ```   

6. Тест для массива 2 * 4 * 3
    - **Input**:
        ```
        2 4 3
        
        18,45 28,43 19,655 28,8904 45,8430 90,2345 45,5454 0,9494 7,9 125 500,54 5,32 0,9 11,09 25,55 30,32 81,88 17,15 19,23 55,11 1 7,23 38,88 11,9        
        ```

    - **Output**:
        ```
         Среднее геом.:
         21,9188
         19,4322
         16,2979
        
         Вывод массива в виде x, y, z: значение
         0, 0, 0: 45.843
         0, 1, 0: 28.43
         0, 2, 0: 19.655
         0, 3, 0: 0.9494
         1, 0, 0: 18.45
         1, 1, 0: 90.2345
         1, 2, 0: 45.5454
         1, 3, 0: 28.8904
         0, 0, 1: 7.9
         0, 1, 1: 11.09
         0, 2, 1: 25.55
         0, 3, 1: 5.32
         1, 0, 1: 0.9
         1, 1, 1: 125.0
         1, 2, 1: 500.54
         1, 3, 1: 30.32
         0, 0, 2: 81.88
         0, 1, 2: 7.23
         0, 2, 2: 38.88
         0, 3, 2: 11.9
         1, 0, 2: 1.0
         1, 1, 2: 17.15
         1, 2, 2: 19.23
         1, 3, 2: 55.11
        
         Массив с округленными эл.:
         45.84 28.43 19.66 0.95 
         18.45 90.23 45.55 28.89 
         ===
         7.9 11.09 25.55 5.32 
         0.9 125.0 500.54 30.32 
         ===
         81.88 7.23 38.88 11.9 
         1.0 17.15 19.23 55.11 
        ```

#За какво си говорихме
+ Функции от по-висок ред върху списъци
 + map
 + filter
 + reduce (fold-left, fold-right)
+ Решихме няколко задачи
 + Среден рейтинг на филми
 + Минимален покриващ правоъгълник по дадени точки
 
Тъй като reduce е нова функция (за нас), ето и примерна дефиниция:
```Scheme
(define (reduce-right op null-value xs)
    (if (null? xs)
        null-value
        (op (car xs) (reduce-right op null-value (cdr xs)))))
```

Това реализира (да кажем) вградената в езика функция fold-right.  
Ето как би изглеждала fold-left

```Scheme
(define (reduce-left op initial xs)
    (if (null? xs)
        initial
        (reduce-left op (op initial (car xs)) (cdr xs)))))
```

Тук трупаме резултата в initial параметъра и по този начин генерираме
опашкова рекурсия (финално рекурентен процес, както му казвате :))

##Последно напомняне за map и filter
+ map е функция, която трансформира списък.  
 + (map f '(1 2 3 4)) -> '((f 1) (f 2) (f 3) (f 4));
+ filter е функция, която филтрира списък по някакъв критерий.

##Условия на задачи
**Задача 1** Нека кажем, че филм за нас означава списък с два елемента, които
са както следва:
1. Заглавие на филм
2. Рейтинг на филм

За даден списък от филми, да се намери средния им рейтинг.  
Да се намери кои филми са с рейтинг, по-голям от средния.

**Идеи:**  
+ Може да вземем всички рейтинги чрез map. Figure it out.  
+ Може да намерим сумата им с reduce. Figure it out.  
+ Може да вземем всички филми с рейтинг, по-висок от средния с filter. Figure it out.  

**Задача 2.** По даден списък с точки от типа '((x1 y1) (x2 y2)...), да се
намери най-малкият правоъгълник, който съдържа в себе си всички подадени точки.

**Идея:** Търсим двойката точки '((min-x min-y) (max-x max-y))
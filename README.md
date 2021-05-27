# projects
# Class List
Реализован класс List, аналогичный std::list<int>. Определены функции push_back, push_front, pop_back, pop_front, size и begin/end, а также конструктор без параметров, оператор присваивания и деструктор. Функции begin и end возвращают итераторы, для которых определены операторы ++, -- и унарный * (разыменование), а также операторы сравнения == и !=.
 
# Class Matrix
 Реализован класс Matrix, содержащий:
1) Оператор вывода
2) Операторы +=, +, *=, *
3) Функции transpose и transposed
4) Функции begin и end, возвращающие итераторы, с помощью которых можно перебрать элементы матрицы построчно. Предусмотрены константная и неконстантная версии.
 
# Class Polynomial
Реализован шаблонный класс Polynomial на основе контейнера std::vector.
1. Написан конструктор:
  + создающий многочлен по заданному вектору коэффициентов.
  + создающий многочлен по заданному коэффициенту (многочлен нулевой степени).
  + создающий многочлен по заданным итераторам на начало и следующий за концом последовательности коэффициентов.
2. Перегружены операторы:
  + [] - коэффициент многочлена перед заданной степенью переменной 
  + ==, !=
  + +, -, +=, -=
  + *, *=
  + () - значение многочлена в точке
  + оператор вывода <<
  + & - композиция
3. Метод Degree для вычисления степени многочлена.
4. Методы begin() и end() для доступа к константным итераторам, позволяющим перебрать коэффициенты многочлена.
 
# Class SharedPtr
Упрощённая реализация класса std::shared_ptr<T>
Предусмотрены следующие функции:
   + Конструктор по умолчанию, создающий пустой умный указатель.
   + Конструктор, принимающий T * и захватывающий владение этой динамической памятью.
   + Конструктор копирования, принимающий на вход другой аналогичный SharedPtr.
   + Конструктор перемещения, получающий на вход rvalue-ссылку на другой SharedPtr и отбирающий у него владение ресурсом.
   + Оператор присваивания, получающий на вход указатель.
   + Оператор присваивания, получающий на вход другой SharedPtr.
   + Move-оператор присваивания, получающий на вход rvalue-ссылку на другой SharedPtr.
   + Деструктор.
   + Константный и неконстантный оператор *.
   + Оператор ->.
   + Функцию void reset(T * ptr), после выполнения которой умный указатель должен уменьшить счётчик ссылок и захватить ptr.
   + Функцию void swap(SharedPtr& other), обменивающуюся содержимым с другим умным указателем.
   + Функцию T * get() const, возвращающую указатель.
   + explicit operator bool() const, позволяющий определить, не пуст ли умный указатель.
 
# Class SharedPtr
Предусмотрены следюущие функции
   + Конструктор по умолчанию, создающий пустой умный указатель.
   + Конструктор, принимающий T * и захватывающий владение этой динамической памятью.
   + Конструктор перемещения, получающий на вход rvalue-ссылку на другой UniquePtr и отбирающий у него владение ресурсом.
   + Оператор присваивания.
   + Move-оператор присваивания, получающий на вход rvalue-ссылку на другой UniquePtr.
   + Деструктор.
   + Константный оператор *.
   + Константный оператор ->.
   + Функцию T * release(), отменяющую владение объектом и возвращающую хранящийся внутри указатель.
   + Функцию void reset(T * ptr), после выполнения которой умный указатель должен захватить ptr.
   + Функцию void swap(UniquePtr& other), обменивающуюся содержимым с другим умным указателем.
   + Функцию T * get() const, возвращающую указатель.
   + explicit operator bool() const, позволяющий определить, не пуст ли умный указатель. 
   + Функция Deleter

# Class Vector
Реализован шаблонный класс Vector, аналогичный std::vector<T>, работающий с динамической памятью.
Предусмотрены следюущие функции
   + Конструктор без параметров.
   + Конструктор копирования.
   + Оператор присваивния.
   + Деструктор.
   + Функции push_back, pop_back, size, operator[].
   + Функции capacity, reserve, resize, clear, swap, begin, end.

 
 

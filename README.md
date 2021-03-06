# Class List
Реализован класс List, аналогичный std::list<int>.
 + Определены функции push_back, push_front, pop_back, pop_front, size и begin/end.
 + Конструктор без параметров, оператор присваивания и деструктор. 
 + Функции begin и end возвращают итераторы, для которых определены операторы ++, -- и унарный * (разыменование)
 + Операторы сравнения == и !=.
 
# Class Matrix
Реализован класс Matrix, содержащий:
 + Оператор вывода
 + Операторы +=, +, *=, *
 + Функции transpose и transposed
 + Функции begin и end, возвращающие итераторы, с помощью которых можно перебрать элементы матрицы построчно. Предусмотрены константная и неконстантная версии.
 
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
   + Функция void reset(T * ptr), после выполнения которой умный указатель должен уменьшить счётчик ссылок и захватить ptr.
   + Функция void swap(SharedPtr& other), обменивающаяся содержимым с другим умным указателем.
   + Функция T * get() const, возвращающая указатель.
   + explicit operator bool() const, позволяющий определить, не пуст ли умный указатель.
 
# Class UniquePtr
Предусмотрены следюущие функции:
   + Конструктор по умолчанию, создающий пустой умный указатель.
   + Конструктор, принимающий T * и захватывающий владение этой динамической памятью.
   + Конструктор перемещения, получающий на вход rvalue-ссылку на другой UniquePtr и отбирающий у него владение ресурсом.
   + Оператор присваивания.
   + Move-оператор присваивания, получающий на вход rvalue-ссылку на другой UniquePtr.
   + Деструктор.
   + Константный оператор *.
   + Константный оператор ->.
   + Функция T * release(), отменяющую владение объектом и возвращающую хранящийся внутри указатель.
   + Функция void reset(T * ptr), после выполнения которой умный указатель должен захватить ptr.
   + Функция void swap(UniquePtr& other), обменивающаяся содержимым с другим умным указателем.
   + Функция T * get() const, возвращающая указатель.
   + explicit operator bool() const, позволяющий определить, не пуст ли умный указатель. 
   + Функция Deleter

# Class Vector
Реализован шаблонный класс Vector, аналогичный std::vector<T>, работающий с динамической памятью.
Предусмотрены следюущие функции:
   + Конструктор без параметров.
   + Конструктор копирования.
   + Оператор присваивния.
   + Деструктор.
   + Функции push_back, pop_back, size, operator[].
   + Функции capacity, reserve, resize, clear, swap, begin, end.

 
 

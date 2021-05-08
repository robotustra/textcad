# textcad

fn == float number

n == name of object

v == variable

str == "quoted_string_without_spaces"

0) Комментарий

	#<any_string>

1) Вещественная переменная

	<fn> <n> VAR

2) Вектор

	<fn|v> <fn|v> <fn|v> <n> VEC	

3) Точка

	<fn|v> <fn|v> <fn|v> <n> DOT

	<vec_name> <n> DOT

4) Кватернион

	<fn|v> <fn|v> <fn|v> <fn|v> <n> QUAT

5) Солид из stl файла

	<str> <n> STL

6) Копия загруженного stl файла в памяти

	<stl_name> <n> COPY

7) Трансляция и поворот для солида. Локальная система координат.

	<vec_name> <quat_name> <n> LCS

8) Трансляция и поворот солида в новую систему координат

	<lcs_name> <stl_name> SETO

9) Присоединение дочернего солида к родительскому. После присоединения все трансляции и повороты,
применяемые к родителю спускаются вниз по дереву дочерних объектов.

	<child_stl_name> <parent_stl_name> NEST

10) Система коордиинат.

	<dot> <vec_x> <vec_y> <vec_z> <n> SOC

11) Линия

	<dot> <dot> <n> LINE

	<dot> <vec> <n> LINE

12) Радиус вектор. Аксиальный вектор. Модуль вектора может быть больше 1. 

	<fn|v> <fn|v> <fn|v> <fn|v> <n> AVEC

13) Окружность. Точка задает центр окружности. 
Аксиальный вектор задает нормаль к плоскости окружности, а четветрая компонента задает радиус.

	<dot> <avec> <n> CIRC

14) Дуга. Точка - начало дуги. Первый аксиальный вектор задает направление касательной в начальной точке,
и радиус дуги. Второй аксиальный вектор задает направление поворота и угол поворота.

	<dot> <avec_1> <avec_2> <n> ARC

15) Путь. Может быть незамкнутым или лежать не в одной плоскости.

	{<dot|line|arc>}+ <n> PATH

16) Плоский замкнутый контур. Система координат переносит и масштабирует путь в соответствии с базисзными векторами. Все точки пути
должны лежать в одной плоскоти. Путь замыкается если был незамкнут. Если система координат не задана, то используется правая система
координат, с началом (0,0,0) и единичными векторами вдоль осей.

	<soc> <path> <n> CONT

	<path> <n> CONT

17) Плоская поверхность. Построение поверхности на заданном контуре.

	<cont> <n> SURF

18) Создание простого солида экструзией. Если при создании поверхности использовался контур с заданной системой координат,
то компоненты вектора будут заданы в этой системе координат.

	<surf> <vec> <n> SOLI

19) Сохранение солида в stl файл.

	<soli> <str> <n> SAVE

20) Сложение солидов.

	<soli_1> <soli_2> <n> BADD

21) Вычитание солидов. [Не реализовано]

	<soli_1> <soli_2> <n> BSUB	

22) Пересечение солидов. [Не реализовано]

	<soli_1> <soli_2> <n> BINT

23) Инверсия пересечения солидов. [Не реализовано]

	<soli_1> <soli_2> <n> BXOR

24) Суммирование контуров. Контуры лежат в одной плоскости.

	<cont_1> <cont_2> <n> CSUM

25) Вычитание контуров, лежащих в одной плоскости. Полученный контур может быть неодносвязный или иметь отверстия.

	<cont_1> <cont_2> <n> CSUB

26) Инвертирование обхода контура. Операция меняет циркуляцию обхода контура на противоположную.

	<cont_1> <n> CINV


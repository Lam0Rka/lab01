## Задание №1
Скачайте библиотеку *boost* с помощью утилиты **wget**. Адрес для скачивания `https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz`.
```sh
wget <Ссылка>
```
Просто скачиваем библиотеку
Библиотека скачена
## Задание №2
Разархивируйте скаченный файл в директорию ~/boost_1_69_0
```sh
tar ~/boost_1_69_0
```
Разархивируем её
## Задание №3
Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
```sh
ls /home/bogdan/boost_1_69_0| wc --l 
16
```
(16 тк я баклажан и ввёл эту команду только на моменте редактирования отчёта)
ls - Выводит нам на экран определённые директории а потом с помощью | wc --l  мы их считаем
## Задание №4
Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
```sh
cd home/bogdan/boost_1_69_0
find ./ -type f | wc -l
61754
```
Тут происходит тоже самое, что и в задании 3
## Задание №5
Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
```sh
(Кол-во заголовочных файлов)
find ./ -type f -name "*.h" | wc -l
299
(Кол-во файлов расширения сpp)
find ./ -type f -name "*.cpp" | wc -l
13803
(Кол-во файлов не расширения .сpp и не .h)
find ./ -type f \( ! -name "*.cpp" ! -name "*.h" \) | wc -l
47652
```
Тоже самое что и в задании три и четыре, только теперь вместо ls команда find и мы ищем определёный формат файла или все файлы но без файлов какого-либо формата
## Задание №6
Найдите полный пусть до файла any.hpp внутри библиотеки boost.
```sh
find "$(cd ..; pwd)" -name "any.hpp"
Вывод:
/home/bogdan/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
/home/bogdan/boost_1_69_0/boost/proto/detail/any.hpp
/home/bogdan/boost_1_69_0/boost/type_erasure/any.hpp
/home/bogdan/boost_1_69_0/boost/any.hpp
/home/bogdan/boost_1_69_0/boost/fusion/include/any.hpp
/home/bogdan/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/home/bogdan/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/home/bogdan/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
/home/bogdan/boost_1_69_0/boost/hana/any.hpp
/home/bogdan/boost_1_69_0/boost/hana/fwd/any.hpp
```
Ну тут комментарии излишне, единственное что, забыл скачать в 5 пункте что -name это поиск файлов по имени
## Задание №7
Выведите в консоль все файлы, где упоминается последовательность boost::asio.
```sh
grep -rnw ./ -e boost::asio 
(Выводятся все файлы, а там их очень очень много)
```
Берём выводим
## Задание №8
Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.
```sh
cd tools/build/
sudo ./bootstrap.sh
./b2 install --prefix=BoostBuild
export PATH=${PATH}:`pwd`/BoostBuild/bin
cd ..
cd ..
b2 --build-dir=/tmp/build-boost toolset=gcc stage
```
Ну тут компилирование буста, единственное, что тут новое это sudo -  это права доступа
## Задание №9
Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
```sh
mv /home/bogdan/boost_1_69_0/boost /home/bogdan/boost_1_69_0/boost-libs
```
Команды mv перемещает выбранную нам папку или файл, в выбранную нами папку
## Задание №10
Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
```sh
du -a -h
(Выводит огромное кол-во файлов и показывает размер каждого из них)
```
du - просто команда, оценивающая вес файла
-a - выбор всех файлов
-h - выводит размер таким образом, чтобы мы понял как он выгляит а-ля: 1К
## Задание №11
Найдите топ10 самых "тяжёлых".
```sh
du -Sh | sort -rh | head -10
(Выводин десять самых "Тяжёлых файлов")
54M	./stage/lib
28M	./libs/math/test
12M	./libs/math/doc
11M	./libs/hana/doc/html
9,4M	./libs/math/doc/graphs
7,6M	./libs/math/doc/equations
7,3M	./libs/gil/doc/html/reference
5,5M	./libs/locale/doc/html
5,3M	./boost-libs/boost/fusion/container/generation/detail/preprocessed
5,2M	./libs/metaparse/doc/images
```
Я уже устал объяснять что тут делает, что я правда устал, время ночь поверьте мне, я знаю что тут происходит
Вы просили написать трудности с которыми столкнулись:
1. Не удавалось скомпилировать boost, но благодаря коллегам, всё-таки проблему решить удалось
2. Очень сложно переключать язык, приходится использовать не просто shift+alt, a shift+alt+a
На этом трудности кончаются

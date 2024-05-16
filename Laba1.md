# Лабораторная работа №1
Все команды выполняются в соответствующих каталогах
### Скачивание boost
~~~
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
> Output:-
~~~
### Разархивируем файл boost в ~/boost_1_69_0
~~~
$ tar -xf boost_1_69_0.tar.gz
Output:-
~~~
### Количество файлов в директории ~/boost_1_69_0 не включая вложенные директории
~~~
$ ls -l ~/boost_1_69_0 | grep -v ^- | wc -l
Output: 16
~~~
### Считая вложенные директории
~~~
$ find ~/boost_1_69_0 -type f | wc -l
Output: 62104
~~~
### Количество заголовочных файлов, файлов с расширением .cpp
~~~
$ find -type f -name "*.cpp" | wc -l
Output: 13786
~~~
### Количество не .cpp и не заголовочных файлов
~~~
$ find . -type f ! -name "*.cpp" ! -name ".hpp" | wc -l
Output: 48318
~~~
### Полный путь до файла any.hpp в библиотеке boost
~~~
$ find $(pwd) -name any.hpp
Output: /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
        /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/boost/type_erasure/any.hpp
        /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/boost/proto/detail/any.hpp
        /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/boost/hana/fwd/any.hpp
        /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/boost/hana/any.hpp
        /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/boost/fusion/include/any.hpp
        /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
        /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
        /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/boost/any.hpp
        /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
~~~
### Все файлы, где упоминается последовательность boost::asio
~~~
$ grep -r -l  -e "boost::asio"
Output: ...
        boost/beast/core/impl/buffers_suffix.ipp
        boost/beast/core/impl/buffers_prefix.ipp
        boost/beast/core/impl/flat_buffer.ipp
        boost/beast/core/impl/buffered_read_stream.ipp
        boost/beast/core/impl/static_buffer.ipp
        boost/beast/core/impl/multi_buffer.ipp
        boost/beast/core/impl/handler_ptr.ipp
        boost/beast/core/impl/read_size.ipp
        boost/beast/core/impl/buffers_adapter.ipp
        boost/beast/core/impl/buffers_cat.ipp
        boost/beast/core/impl/flat_static_buffer.ipp
        boost/beast/core/flat_buffer.hpp
        boost/beast/core/ostream.hpp
        boost/beast/core/buffered_read_stream.hpp
        boost/beast/core/buffers_cat.hpp
        boost/beast/core/buffers_to_string.hpp
        boost/beast/core/buffers_adapter.hpp
        boost/beast/core/type_traits.hpp
        boost/beast/core/buffers_prefix.hpp
        boost/beast/core/multi_buffer.hpp
~~~
### Компиляция boost
~~~
$ ./bootstrap.sh --prefix=/home/georgiy/3Wc4YEM5/workspace/temp
$ ./b2 install
$ mv /home/ezh/3Wc4YEM5/workspace/boost_1_69_0/temp boost-libs
$ rm /home/ezhvkh/3Wc4YEM5/workspace/boost_1_69_0/temp
Output:-
~~~
### Вес каждого файла по отдельности
~~~
$ find ~/boost-libs -type f -exec du -Sh {} \;
Output: ...
        4,0K	./include/boost/mp11/detail/mp_plus.hpp
        4,0K	./include/boost/mp11/detail/mp_min_element.hpp
        4,0K	./include/boost/mp11/map.hpp
        4,0K	./include/boost/mp11/set.hpp
        8,0K	./include/boost/mp11/utility.hpp
        8,0K	./include/boost/mp11/list.hpp
        4,0K	./include/boost/mp11/function.hpp
        4,0K	./include/boost/mp11/tuple.hpp
        4,0K	./include/boost/mp11/bind.hpp
        4,0K	./include/boost/mp11/integral.hpp
        4,0K	./include/boost/mp11/integer_sequence.hpp
        4,0K	./include/boost/mp11/mpl.hpp
~~~
### 10 самых тяжёлых файлов
~~~
$ find ~/boost-libs -type f -exec du -Sh {} + | sort -rh | head -10
Output: 4,6M	./lib/libboost_wave.a
        2,8M	./lib/libboost_math_tr1l.a
        2,8M	./lib/libboost_math_tr1f.a
        2,8M	./lib/libboost_math_tr1.a
        2,7M	./lib/libboost_regex.a
        2,3M	./lib/libboost_unit_test_framework.a
        2,3M	./lib/libboost_test_exec_monitor.a
        2,3M	./include/boost/typeof/vector200.hpp
        2,1M	./lib/libboost_locale.a
        1,9M	./include/boost/geometry/srs/projections/epsg_traits.hpp
~~~
~~~
ИУ8-25 Маланичев Александр
~~~

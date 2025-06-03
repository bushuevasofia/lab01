## Homework I

1. Скачайте библиотеку *boost* с помощью утилиты **wget**. Адрес для скачивания `https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz`.
   - Команда: ```wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz" ```  
Вывод команды:
```sh
--2025-06-02 18:43:34--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download
Resolving sourceforge.net (sourceforge.net)... 104.18.13.149, 104.18.12.149, 2606:4700::6812:c95, ...
Connecting to sourceforge.net (sourceforge.net)|104.18.13.149|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABoPikWssHvRegbsx3NAArPSxazhPlgC7rxvhKnk9qH2BtjC8oMDjQwj8UIMHrHxlIhH4XM3xza4c8VDUaDHvhv9LGknw%3D%3D&use_mirror=altushost-swe&r= [following]
--2025-06-02 18:43:34--  https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABoPikWssHvRegbsx3NAArPSxazhPlgC7rxvhKnk9qH2BtjC8oMDjQwj8UIMHrHxlIhH4XM3xza4c8VDUaDHvhv9LGknw%3D%3D&use_mirror=altushost-swe&r=
Resolving downloads.sourceforge.net (downloads.sourceforge.net)... 104.18.12.149, 104.18.13.149, 2606:4700::6812:c95, ...
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|104.18.12.149|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://altushost-swe.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1 [following]
--2025-06-02 18:43:35--  https://altushost-swe.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1
Resolving altushost-swe.dl.sourceforge.net (altushost-swe.dl.sourceforge.net)... 79.142.76.130
Connecting to altushost-swe.dl.sourceforge.net (altushost-swe.dl.sourceforge.net)|79.142.76.130|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 111710205 (107M) [application/x-gzip]
Saving to: ‘boost_1_69_0.tar.gz’

boost_1_69_0.tar.gz                                        100%[========================================================================================================================================>] 106.53M  5.40MB/s    in 22s     

2025-06-02 18:43:58 (4.79 MB/s) - ‘boost_1_69_0.tar.gz’ saved [111710205/111710205]

```
2. Разархивируйте скаченный файл в директорию `~/boost_1_69_0`
   - Команда: ```tar -xf boost_1_69_0.tar.gz -C ~/ ```   
3. Подсчитайте количество файлов в директории `~/boost_1_69_0` **не включая** вложенные директории.
   - Команда: ```find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l```  
Вывод: ```12```
4. Подсчитайте количество файлов в директории `~/boost_1_69_0` **включая** вложенные директории.
   - Команда: ```find ~/boost_1_69_0 -type f | wc -l```  
Вывод: ```61863```
5. Подсчитайте количество заголовочных файлов, файлов с расширением `.cpp`, сколько остальных файлов (не заголовочных и не `.cpp`).
   - Команда: ```hpp_count=$(find . -type f -name "*.hpp" | wc -l)
     echo "Заголовочных файлов (.hpp): $hpp_count"```  
Вывод: ```Заголовочных файлов (.hpp): 14912```
   - Количество файлов типа '.cpp'. Команда: ```cpp_count=$(find . -type f -name "*.cpp" | wc -l)
     echo "Файлов .cpp: $cpp_count" ```  
Вывод: ```13774 ```
   - Количество остальных файлов. Команда: ```other_count=$(( $(find . -type f | wc -l) - $hpp_count - $cpp_count ))
echo "Остальных файлов: $other_count" ```  
Вывод: ```32505```
6. Найдите полный путь до файла `any.hpp` внутри библиотеки *boost*. Команда: ```find ~/boost_1_69_0 -type f -name any.hpp```  
```sh
/home/kali/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
/home/kali/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
/home/kali/boost_1_69_0/boost/type_erasure/any.hpp
/home/kali/boost_1_69_0/boost/any.hpp
/home/kali/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/home/kali/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/home/kali/boost_1_69_0/boost/fusion/include/any.hpp
/home/kali/boost_1_69_0/boost/proto/detail/any.hpp
/home/kali/boost_1_69_0/boost/hana/fwd/any.hpp
/home/kali/boost_1_69_0/boost/hana/any.hpp
```
7. Выведите в консоль все файлы, где упоминается последовательность `boost::asio`.  
Команда: ```grep -rl "boost::asio" ~/boost_1_69_0```  
Вывод (будет ссылка).
8. Скомпилирутйе *boost*. Можно воспользоваться [инструкцией](https://www.boost.org/doc/libs/1_61_0/more/getting_started/unix-variants.html#or-build-custom-binaries) или [ссылкой](https://codeyarns.com/2017/01/24/how-to-build-boost-on-linux/).  
Команды:  
```sh
cd ~/boost_1_69_0
./bootstrap.sh --prefix=./build
./b2 --build-dir=build stage
```
Вывод (сссылка).  
9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boost-libs`.  
```sh
mkdir ~/boost-libs

cp lib/*.a ~/boost-libs

ls ~/boost-libs
```  
Создали папку, скопировали и вывели содержимое. Вывод:  
```sh
libboost_atomic.a     libboost_contract.a   libboost_filesystem.a        libboost_program_options.a  libboost_stacktrace_addr2line.a  libboost_system.a               libboost_wave.a
libboost_chrono.a     libboost_date_time.a  libboost_graph.a             libboost_random.a           libboost_stacktrace_backtrace.a  libboost_test_exec_monitor.a    libboost_wserialization.a
libboost_container.a  libboost_exception.a  libboost_iostreams.a         libboost_regex.a            libboost_stacktrace_basic.a      libboost_timer.a
libboost_context.a    libboost_fiber.a      libboost_prg_exec_monitor.a  libboost_serialization.a    libboost_stacktrace_noop.a       libboost_unit_test_framework.a

```
10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.  
Команда: ```du -ah ~/boost-libs```   
Вывод:
```sh
4.5M    /home/kali/boost-libs/libboost_wave.a
232K    /home/kali/boost-libs/libboost_fiber.a
272K    /home/kali/boost-libs/libboost_iostreams.a
152K    /home/kali/boost-libs/libboost_container.a
2.2M    /home/kali/boost-libs/libboost_test_exec_monitor.a
152K    /home/kali/boost-libs/libboost_date_time.a
80K     /home/kali/boost-libs/libboost_random.a
3.1M    /home/kali/boost-libs/libboost_regex.a
2.2M    /home/kali/boost-libs/libboost_unit_test_framework.a
400K    /home/kali/boost-libs/libboost_filesystem.a
1.2M    /home/kali/boost-libs/libboost_serialization.a
4.0K    /home/kali/boost-libs/libboost_atomic.a
232K    /home/kali/boost-libs/libboost_chrono.a
320K    /home/kali/boost-libs/libboost_contract.a
824K    /home/kali/boost-libs/libboost_graph.a
52K     /home/kali/boost-libs/libboost_timer.a
4.0K    /home/kali/boost-libs/libboost_stacktrace_noop.a
20K     /home/kali/boost-libs/libboost_stacktrace_backtrace.a
776K    /home/kali/boost-libs/libboost_wserialization.a
36K     /home/kali/boost-libs/libboost_stacktrace_addr2line.a
4.0K    /home/kali/boost-libs/libboost_system.a
20K     /home/kali/boost-libs/libboost_context.a
16K     /home/kali/boost-libs/libboost_stacktrace_basic.a
208K    /home/kali/boost-libs/libboost_prg_exec_monitor.a
1.5M    /home/kali/boost-libs/libboost_program_options.a
4.0K    /home/kali/boost-libs/libboost_exception.a
```
11. Найдите *топ10* самых "тяжёлых".
Команда: ```find ~/boost-libs -type f -exec du -h {} + | sort -hr | head -n 10```   
Вывод:
```sh
4.5M    /home/kali/boost-libs/libboost_wave.a
3.1M    /home/kali/boost-libs/libboost_regex.a
2.2M    /home/kali/boost-libs/libboost_unit_test_framework.a
2.2M    /home/kali/boost-libs/libboost_test_exec_monitor.a
1.5M    /home/kali/boost-libs/libboost_program_options.a
1.2M    /home/kali/boost-libs/libboost_serialization.a
824K    /home/kali/boost-libs/libboost_graph.a
776K    /home/kali/boost-libs/libboost_wserialization.a
400K    /home/kali/boost-libs/libboost_filesystem.a
320K    /home/kali/boost-libs/libboost_contract.a
```

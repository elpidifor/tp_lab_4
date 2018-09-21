# tp_lab_4


Данная лабораторная работа посвещена изучению систем автоматизации сборки проекта на примере **CMake**

```ShellSession
$ open https://cmake.org/
```

## Tasks

- [ ] 1. Создать публичный репозиторий с названием **lab04** на сервисе **GitHub**
- [ ] 2. Ознакомиться со ссылками учебного материала
- [ ] 3. Выполнить инструкцию учебного материала
- [ ] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```ShellSession
$ export GITHUB_USERNAME=<имя_пользователя> // Экспорт
```

```ShellSession
$ cd ${GITHUB_USERNAME}/workspace // Перход в воркспейс
$ pushd . // Сохраняем путь в стеке
```

```ShellSession
$ git clone https://github.com/${GITHUB_USERNAME}/lab03.git projects/lab04 // Клонируем задание
$ cd projects/lab04 // Переход
$ git remote remove origin // Обнуляем ориджин
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab04.git // Привязываем новый
```

```ShellSession
$ g++ -I./include -std=c++11 -c sources/print.cpp // Только компилируем print.cpp, стандарт С++ 2011
$ ls print.o /* print.o */
$ nm print.o | grep print // Выводит нахождения print в файлах
/* 0000000000000000 T __Z5printRKNSt3__112basic_stringIcNS_11char_traitsIcEENS_9allocatorIcEEEERNS_13basic_ostreamIcS2_EE
0000000000000210 T __Z5printRKNSt3__112basic_stringIcNS_11char_traitsIcEENS_9allocatorIcEEEERNS_14basic_ofstreamIcS2_EE */
$ ar rvs print.a print.o // Архивируем файл print.o
/* creating archive print.a */
$ file print.a // Определяем тип файла 
/* print.a: current ar archive random library */
$ g++ -I./include -std=c++11 -c examples/example1.cpp // Только компилируем example1.cpp, стандарт С++ 2011
$ ls example1.o // Содержание 
/* example1.o */
$ g++ example1.o print.a -o example1 // Компиляция и запуск
$ ./example1 && echo // Запуск и вывод
/* hello */
```

```ShellSession
$ g++ -I./include -std=c++11 -c examples/example2.cpp // Компилируем
$ nm example2.o // Вывод символов
/* 000000000000379c s GCC_except_table0
0000000000003870 s GCC_except_table29
00000000000037f0 s GCC_except_table7
0000000000003824 s GCC_except_table8
                 U __Unwind_Resume
                 U __Z5printRKNSt3__112basic_stringIcNS_11char_traitsIcEENS_9allocatorIcEEEERNS_14basic_ofstreamIcS2_EE
                 U __ZNKSt3__16locale9has_facetERNS0_2idE
                 U __ZNKSt3__16locale9use_facetERNS0_2idE
0000000000003030 T __ZNSt3__111char_traitsIcE11eq_int_typeEii
0000000000003020 T __ZNSt3__111char_traitsIcE11to_int_typeEc
00000000000030d0 T __ZNSt3__111char_traitsIcE12to_char_typeEi
00000000000030a0 T __ZNSt3__111char_traitsIcE2eqEcc
0000000000002ef0 T __ZNSt3__111char_traitsIcE3eofEv
0000000000003780 T __ZNSt3__111char_traitsIcE6lengthEPKc
0000000000003050 T __ZNSt3__111char_traitsIcE7not_eofEi
                 U __ZNSt3__112basic_stringIcNS_11char_traitsIcEENS_9allocatorIcEEE6__initEPKcm
                 U __ZNSt3__112basic_stringIcNS_11char_traitsIcEENS_9allocatorIcEEED1Ev
0000000000002f00 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE11__read_modeEv
00000000000030f0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE12__write_modeEv
0000000000003260 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE4openEPKcj
0000000000001750 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE4syncEv
00000000000006a0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE5closeEv
0000000000000b00 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE5imbueERKNS_6localeE
0000000000000d40 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE6setbufEPcl
0000000000001030 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE7seekoffExNS_8ios_base7seekdirEj
0000000000001500 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE7seekposENS_4fposI11__mbstate_tEEj
00000000000028b0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE8overflowEi
0000000000002760 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE9pbackfailEi
0000000000001da0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE9underflowEv
0000000000003240 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEEC1Ev
0000000000003530 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEEC2Ev
0000000000000ad0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEED0Ev
0000000000000580 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEED1Ev
00000000000005a0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEED2Ev
                 U __ZNSt3__113basic_ostreamIcNS_11char_traitsIcEEED0Ev
                 U __ZNSt3__113basic_ostreamIcNS_11char_traitsIcEEED1Ev
                 U __ZNSt3__113basic_ostreamIcNS_11char_traitsIcEEED2Ev
0000000000000520 T __ZNSt3__114basic_ofstreamIcNS_11char_traitsIcEEED0Ev
0000000000000440 T __ZNSt3__114basic_ofstreamIcNS_11char_traitsIcEEED1Ev
0000000000000480 T __ZNSt3__114basic_ofstreamIcNS_11char_traitsIcEEED2Ev
                 U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEE5uflowEv
                 U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEE6xsgetnEPcl
                 U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEE6xsputnEPKcl
                 U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEE9showmanycEv
                 U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEEC2Ev
                 U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEED2Ev
                 U __ZNSt3__16localeC1ERKS0_
                 U __ZNSt3__16localeD1Ev
                 U __ZNSt3__17codecvtIcc11__mbstate_tE2idE
                 U __ZNSt3__18ios_base4initEPv
                 U __ZNSt3__18ios_base5clearEj
                 U __ZNSt3__19basic_iosIcNS_11char_traitsIcEEED2Ev
                 U __ZNSt8bad_castC1Ev
                 U __ZNSt8bad_castD1Ev
                 U __ZSt9terminatev
0000000000003970 D __ZTCNSt3__114basic_ofstreamIcNS_11char_traitsIcEEEE0_NS_13basic_ostreamIcS2_EE
0000000000003a60 D __ZTINSt3__113basic_filebufIcNS_11char_traitsIcEEEE
                 U __ZTINSt3__113basic_ostreamIcNS_11char_traitsIcEEEE
00000000000039c0 D __ZTINSt3__114basic_ofstreamIcNS_11char_traitsIcEEEE
                 U __ZTINSt3__115basic_streambufIcNS_11char_traitsIcEEEE
                 U __ZTISt8bad_cast
0000000000003ab0 S __ZTSNSt3__113basic_filebufIcNS_11char_traitsIcEEEE
0000000000003a80 S __ZTSNSt3__114basic_ofstreamIcNS_11char_traitsIcEEEE
0000000000003950 D __ZTTNSt3__114basic_ofstreamIcNS_11char_traitsIcEEEE
                 U __ZTVN10__cxxabiv120__si_class_type_infoE
00000000000039d8 D __ZTVNSt3__113basic_filebufIcNS_11char_traitsIcEEEE
0000000000003900 D __ZTVNSt3__114basic_ofstreamIcNS_11char_traitsIcEEEE
                 U __ZTVNSt3__18ios_baseE
                 U __ZTVNSt3__19basic_iosIcNS_11char_traitsIcEEEE
                 U __ZTv0_n24_NSt3__113basic_ostreamIcNS_11char_traitsIcEEED0Ev
                 U __ZTv0_n24_NSt3__113basic_ostreamIcNS_11char_traitsIcEEED1Ev
0000000000000550 T __ZTv0_n24_NSt3__114basic_ofstreamIcNS_11char_traitsIcEEED0Ev
00000000000004f0 T __ZTv0_n24_NSt3__114basic_ofstreamIcNS_11char_traitsIcEEED1Ev
                 U __ZdaPv
                 U __ZdlPv
                 U __Znam
0000000000000ac0 T ___clang_call_terminate
                 U ___cxa_allocate_exception
                 U ___cxa_begin_catch
                 U ___cxa_end_catch
                 U ___cxa_throw
                 U ___gxx_personality_v0
                 U ___stack_chk_fail
                 U ___stack_chk_guard
                 U _fclose
                 U _fflush
                 U _fopen
                 U _fread
                 U _fseek
                 U _fseeko
                 U _ftello
                 U _fwrite
0000000000000000 T _main
                 U _memcpy
                 U _memmove
                 U _memset
                 U _strlen
 */
$ g++ example2.o print.a -o example2 // Компиляция
$ ./example2 // Запуск
$ cat log.txt && echo // Открытие и вывод
/* hello */
```

```ShellSession
// Удаляем созданные файлы
$ rm -rf example1.o example2.o print.o 
$ rm -rf print.a 
$ rm -rf example1 example2
$ rm -rf log.txt
```

```ShellSession
// Добавляем строчки в CMakeLists.txtx
$ cat > CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.0)
project(print)
EOF
```

```ShellSession
$ cat >> CMakeLists.txt <<EOF
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
EOF
```

```ShellSession
$ cat >> CMakeLists.txt <<EOF
add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
EOF
```

```ShellSession
$ cat >> CMakeLists.txt <<EOF
include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
EOF
```

```ShellSession
$ cmake -H. -B_build
$ cmake --build _build
```

```ShellSession
$ cat >> CMakeLists.txt <<EOF

add_executable(example1 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example1.cpp)
add_executable(example2 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)
EOF
```

```ShellSession
$ cat >> CMakeLists.txt <<EOF

target_link_libraries(example1 print)
target_link_libraries(example2 print)
EOF
```

```ShellSession
// Компилиуем с заданными параметрами сборки
$ cmake --build _build
$ cmake --build _build --target print
$ cmake --build _build --target example1
$ cmake --build _build --target example2
```

```ShellSession
$ ls -la _build/libprint.a // Выводим содержимое
$ _build/example1 && echo // Вывод в консоль
hello
$ _build/example2
$ cat log.txt && echo // Открытие и вывод в консоль
hello
$ rm -rf log.txt // Удаляем текстовик
```

```ShellSession
$ git clone https://github.com/tp-labs/lab04 tmp // Клонируем репозиторий в папку tmp
/* Cloning into 'tmp'...
remote: Counting objects: 37, done.
remote: Total 37 (delta 0), reused 0 (delta 0), pack-reused 37
Unpacking objects: 100% (37/37), done. */
$ mv -f tmp/CMakeLists.txt . // Перемещение файла
$ rm -rf tmp // Удаление папка
```

```ShellSession
// Редактируем CMakeLists.txt
$ cat CMakeLists.txt
$ cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
$ cmake --build _build --target install
$ tree _install
/* _install
├── cmake
│   ├── print-config-noconfig.cmake
│   └── print-config.cmake
├── include
│   └── print.hpp
└── lib
    └── libprint.a */
```

```ShellSession
$ git add CMakeLists.txt // Staged
$ git commit -m"added CMakeLists.txt" // Committed
$ git push origin master // Pushed
```

## Report

```ShellSession
$ popd // Выгруз пути из стека
// Создание отчёта
$ export LAB_NUMBER=04
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m "lab${LAB_NUMBER}"
```

## Links

- [Autotools](http://www.gnu.org/software/automake/manual/html_node/Autotools-Introduction.html)
- [CMake](https://cgold.readthedocs.io/en/latest/index.html)

```
Copyright (c) 2017 Братья Вершинины
```

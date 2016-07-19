Содержание проекта
========================
Проект состоит из нескольких скриптов, описание каждого из которых будет приведено ниже:
* Splitting
- Classification
- Heuristics
- Multialignment
- HMM

Splitting
------------------------
Программа получает на вход fasta-файл и выходную директорию, а затем разделяет полученный на вход файл на несколько файлов фиксированной длины. Ключи программы:
  * `--in_file` (полный путь до входного файла)
  - `--out_dir` (полный путь до папки, куда скрипт перепишет полученные файлы)
  - `--len_spl` (длина последовательностей, на которые программа разобъёт входной файл)

Classification
---------------------
Программа получает на вход файл, а также тип цепи иммуноглобулинов, которые должны лежать в данном файле - LC (light cahin) или HC (heavy chain). Программа для каждой последовательности файла перебирает все шесть типов сбивки рамки считывания - на 0, 1, 2 для каждого из двух прочтений - прямого и обратного. Если программа находит каком-то смещении все четыре FR региона при транслировании последовательности в аминокислоты, то она записывает её в файл good, если 2-3 FR - региона совпали, то отправляет в файл bad, иначе - в файл trash. Ключи программы:
  * `--in_file` (полный путь до входного файла)
  - `--out_dir` (полный путь до папки, куда скрипт перепишет полученные файлы)
  - `--path_germlines` (полный путь до папки с FR - регионами)
  - `--is_heavy` (1 если обрабатываемый файл содержит LC иначе - 0)
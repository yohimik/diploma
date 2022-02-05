# Пояснительная записка

Документ основан на [ГОСТ 7.32-2001 и ГОСТ РВ 15.110-2003](https://github.com/latex-g7-32/latex-g7-32)

## Сборка

Пример с использованием `pdfLaTeX`:
```shell
pdflatex -file-line-error -interaction=nonstopmode -synctex=1 -output-format=pdf -output-directory=/output/dir/ main.tex
bibtex main
pdflatex -file-line-error -interaction=nonstopmode -synctex=1 -output-format=pdf -output-directory=/output/dir/ main.tex
pdflatex -file-line-error -interaction=nonstopmode -synctex=1 -output-format=pdf -output-directory=/output/dir/ main.tex
```

### tikz-uml

Файл `tikz-uml.sty` содержит исходный код пакета `tikz-uml` с поддержкой кириллицы.


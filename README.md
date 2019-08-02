# :penguin: Expressões Regulares
##### _Professor Júlio Cezar Neves_ [Aula](https://www.youtube.com/watch?v=dfq1QVqqiGY)
É um método formal de se especificar um padão de texto
Mareiras de procucar, alterar e/ou modelar um texto


### Metacaracteres
Grupo|Meta|Mnemônico|Obs
:---:|:---:|---|---
**Representantes**|\.|ponto|Qualquer caracter.
representa um ou|[ ]|lista|Apenas o que coincidir. Não existe coringa
mais caracteres|[^]|lista negada|Inverte a lógica
**Quantificadores**|?|opcional|O caractere ou lista anterior ficam opcionais
"|*|asterisco|A entidade anterior apareça em qualquer quantidade. De 0 a ∞
"|+|mais|
"|{ }|chaves
Âncoras|^|circunflexo
"|$|cifrão
"|\\b|borda
Outros|\\|escape
"|\||ou
"|( )|grupo
"|\\n|retrovisor

### Classe POSIX
_Respeita o idioma_
```console
$ grep -o \[[:lower:]] <<< ação
$ ação
$ grep -o [a-z] <<< ação
$ ao
``` 

classe POSIX|Similar|Significado
:------:|:------:|------------------
[:upper:]|[A-Z]|letras maiúsculas
[:lower:]|[a-z]|letras minúsculas
[:alpha:]|[A-Za-z]|maiúsculas/minúsculas
[:alnum:]|[A-Za-z0-9]|letras e números
[:digit:]|[0-9]|números
[:xdigit:]|[0-9A-Fa-f]|números hexadecimais
[:punct:]|[.,!?:...]|sinais de pontuação
[:blank:]|[ \t]|espaço e TAB
[:space:]|[ \t\n\r\f\v]|caracteres brancos
[:cntrl:]|-|caracteres de controle
[:graph:]|[^ \t\n\r\f\v]|caracteres imprimíveis
[:print:]|[^\t\n\r\f\v]|imprimíveis e o espaço

### Sequência de escape (ou atalho de classe)
*Escape*|*Significado*
:---:|---
\s|Equivale espaços em branco, \r ou \t
\S|Negação do \s
\w|Equivale letra, digito, ou '_'
\W|Negação de \w
\d|Números - quando usando o **grep** com a opção **-P** (Perl)
\D|Negação de \d


##### Shell Script
```bash
#!/bin/bash

# transforma um arquivo padrão DOS para o formato Linux
# removendo CR - carriage return (^M)

# tr - modifica ou apaga caractere
# tee - mostra na tela e salva no arquivo
# test - integrado ao if pelo [] para testar argumentos

if [ -e ${1} ]
then
	echo Antes
	cat -A ${1}
	file ${1}
	echo Depois
	tr -d '\r' < ${1} | tee ${1}.lx | cat -A
	file ${1}.lx
else
	echo Arquivo não existe
fi
```
##### [Control character](https://en.wikipedia.org/wiki/Control_character)
```
The control characters in ASCII still in common use include:

- 0 (null, NUL, \0, ^@), originally intended to be an ignored character, but now used by many programming languages including C to mark the end of a string.
- 7 (bell, BEL, \a, ^G), which may cause the device to emit a warning such as a bell or beep sound or the screen flashing.
- 8 (backspace, BS, \b, ^H), may overprint the previous character.
- 9 (horizontal tab, HT, \t, ^I), moves the printing position right to the next tab stop.
- 10 (line feed, LF, \n, ^J), moves the print head down one line, or to the left edge and down. Used as the end of line marker in most UNIX systems and variants.
- 11 (vertical tab, VT, \v, ^K), vertical tabulation.
- 12 (form feed, FF, \f, ^L), to cause a printer to eject paper to the top of the next page, or a video terminal to clear the screen.
- 13 (carriage return, CR, \r, ^M), moves the printing position to the start of the line, allowing overprinting. Used as the end of line marker in Classic Mac OS, OS-9, FLEX (and variants). A CR+LF pair is used by CP/M-80 and its derivatives including DOS and Windows, and by Application Layer protocols such as FTP, SMTP, and HTTP.
- 26 (Control-Z, SUB, EOF, ^Z). Acts as an end-of-file for the Windows text-mode file i/o.
- 27 (escape, ESC, \e (GCC only), ^[). Introduces an escape sequence.
```

### Lista Negada
Possui a lógica inversa quando o **circunflexo (^)** é
colocado no incício da lista.  
Ex.: **[^0-9]** equivale a tudo menos os números.


Pausado em 34min. Continua...


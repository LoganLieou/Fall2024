# Flex

This page will contain notes related to flex. Flex is made up of 3 sections the
first section will contain some C code usually global variables and includes,
then second section will contain rules this section starts and ends with `%%` in
here the rules are of form `regex {...}` where inside `{}` is some C code.
finally the third section is additional C code generically:
```c
int main(void) {
    yylex();
    return 0;
}
```

## Various Examples

Lexing N words, professor points out something interesting I didn't realize here
if you don't explicitly handle certain inputs you may get some buggy output so
here we get a newline before outputting `Words: 3` on input `word1 word2 word3`
in order to resolve this must handle whitespace I guess idk how this works
though.
```c
%{
#include <stdio.h>
int word_count = 0;
%}

%%
[a-zA-Z]+ { printf("received a word!\n"); word_count++; }
. /* ignore everything else */
%%

int main(void) {
    yylex();
    printf("Words: %d\n", word_count);
    return 0;
}
```
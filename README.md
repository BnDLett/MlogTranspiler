An mlog transpiler with support for macros and simple counter arrays.

The program takes some arguments, `-src` for the input file, `-out` for the output file, `-copy` to enable copying to clipboard, and `-no_scope` to disable scope. Everything but the input file is optional.

Macros are like functions, you define them with `mac define Name arg1 ...` then your code, then a `mac end`. Macros can be called with `mac Name arg1 ...`. They also have individual scope, to interact with variables outside the macro use `$variable`.

`const` will allow you to define words to other things, any instance of the word in the code will be replaced by the defined replacement.

`cop` behaves like `op` but is eveluated at transpile time

The `include` instruction allows you to include another file, and use it's macros. included macros will also apply their own includes. To include a file use `include filePath`, the file path is relative to the directory of the initial file.

Arrays are an easy way to utilize counter arrays, and can be defined with `arr define Name size`. They can be read with `arr read Name output index`, and written to with `arr write Name input index` 

It also adds a few smaller instructions:

`swrite` writes a constant string to a memcell as ascii values.
`printf` converts a formatted string into a series of prints.

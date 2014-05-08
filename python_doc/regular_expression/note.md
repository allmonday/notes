#Regular Expressions

##Special characters  
characters | description | example
-----|------| --------
. | 匹配除了`newline`以外所有字符(DOTALL:匹配所有)  |
^ | 字符为起始字符(MULTILINE:还匹配换行后的)  |
$ | 字符串为结束字符(MULTILINE：还匹配换行前的)| foo.$ => 'foo1\nfoo2\n' => foo2
\* | 匹配 0 或 n 次 | `ab*`: 'a','ab','abbb'
\+ | 匹配 1 或 n 次 |  `ab+`: 'ab', 'abbb'
\? | 只匹配 0 或 1 次 | `ab?`: 'a','ab'
\*?, +? ,?? | 非贪婪模式 | `<.*?>`  
\{m\} | 匹配m次 |
\{m, n\} | 匹配m 到 n 次 |
\{m, n\} | 最小匹配模式 | 
\\ | 转义 | 



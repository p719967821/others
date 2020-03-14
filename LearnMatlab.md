1.数学中ln在matlab中用log表示，即matlab中输入log(3)，结果为ln3的解，数学中lg用log10()表示，其他一样为logm()
2.Π（pai）在matlab中直接打pi即可，自然对数e用exp()来表示,e^3用exp(3)表示。
3.输入who可以看到变量，whos可以看到变量的更多信息。
4.Inf，eps，NaN，pi等（输入iskeyword可查看）都被用掉不能做变量
5.format xx可以使显示变得不同，默认为short显示小数点后四位，变成long的话可以显示的更长。还有longE，用科学计数法显示更长，bank
6.表示矩阵中的数，如果只用一个数，是竖着的开始的a(num)，如果是两个数，是从1开始，而不是从0开始a(row,col)
7.还有几个特殊的函数eye，zeros，diag等等
# webpack 中有三种hash

| 名称 | 区别 |
| -- | -- |
| hash | hash是项目级别的，他的缺点是假如我只改了其中一个文件，但是所有文件的文件名里面的hash都是一样的 | 
| chunkhash | 针对entry的每一个入口文件，独立的hash。如果entry里面的其中一个文件内容改变，只会改变这个入口文件build之后的文件名，而不会影响到其他文件 | 
| contenthash | 要文件内容不一样，产生的哈希值就不一样 |    
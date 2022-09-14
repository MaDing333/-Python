# 合肥工业大学信息论与编码课程设计，含代码，可视化界面，课设报告

## 必做题

对任意输入的字符串序列分别进行二元霍夫曼编码、fano 编码、游程编码和 算术编码，给出编码结果、编码效率；并实现相应的译码操作。

## 选做题

对一幅BMP格式的灰度图像先进行二元霍夫曼编码和游程编码，并根据霍夫曼编码结果将游程编码变换成二进制序列。（象素用霍夫曼编码，游程用等长码）。并设计相应的译码。

## 开发工具和环境

```python
# 编辑工具：Visual Studio Code
# 编译工具：python 3.9.7
# 界面工具：PyQt5 designer
# 用到的库：math; Pillow 8.4.0; PyQt5 5.15.4;
```

## 模块划分

由下图可见，有五个按钮，分别实现五个题目对应的功能，分别调用五个python 文件来进行对应的编码。在文本框中输入被编码的字符串，点击不同的按钮，即可得到字符及其对应的编码，编码结果，译码结果和编码效率。Huffman编码为Huffman.py，Fano编码为fano.py, 游程编码为run_length2.py, 算数编码为signal.py, 灰度图像编码为bmp_huffman.py，主界面源文件为main.ui和UI_main.py, 主函数为main.py 负责将编码程序和界面程序统一管理。下图为软件主窗口图：

![image-20220718085420192](D:\csdn资源包\我上传的\csdn.assets\image-20220718085420192.png)                   

以下为各个子文件的模块划分：

## Huffman.py 模块的划分

| 函数名称              | 函数输入                 | 函数输出                         |
| --------------------- | ------------------------ | -------------------------------- |
| Class node            | Huffman结点参数          | 一个结点                         |
| get_text_count()      | 被编码的字符串           | 字符和相应概率                   |
| create_nodes()        | 字符串的字符             | 结点列表                         |
| create_huffman_tree() | 结点列表                 | Huffman树和根结点                |
| huffman_encoding()    | 字符频率和Huffman树      | 每个结点被编成的字符串和平均码长 |
| encode_str()          | 文本和结点列表           | 被编码的字符串                   |
| decode_str()          | 被编码的字符串和结点列表 | 解码后的字符串                   |
| get_H()               | 字符和相应的概率         | 信源的熵                         |

## fano.py模块的划分

| 函数名称                  | 函数输入               | 函数输出               |
| ------------------------- | ---------------------- | ---------------------- |
| Class node                | fano结点参数           | 一个结点               |
| get_text_count()          | 被编码的字符串         | 字符和相应概率         |
| create_nodes()            | 字符串的字符           | 结点列表               |
| fano_encode()             | 结点列表和字符相应概率 | 每个结点被编成的字符串 |
| encode_str()              | 文本和结点列表         | 被编码的字符串         |
| decode_str()              | 被编码字符串结点列表   | 解码后的字符串         |
| get_H()                   | 字符和相应的概率       | 信源的熵               |
| get_average_code_length() | 结点列表               | 平均码长               |

## run_lenggth2.py模块划分

| 函数名称             | 函数输入                 | 函数输出               |
| -------------------- | ------------------------ | ---------------------- |
| get_text_count()     | 被编码的字符串           | 字符和相应概率         |
| get_max_bin_length() | 被编码的字符串           | 游程码的最大二进制长度 |
| encode_str()         | 被编码的字符串和游程列表 | 被编码的字符串         |
| decode_str()         | 被编码字符串和游程列表   | 解码后的字符串         |
| get_H()              | 字符和相应的概率         | 信源的熵               |

## signal.py模块的划分

| 函数名称         | 函数输入                       | 函数输出                           |
| ---------------- | ------------------------------ | ---------------------------------- |
| get_text_count() | 被编码的字符串                 | 字符及相应概率和信源的熵和平均码长 |
| encode_str()     | 被编码的字符串和字符相应的概率 | 被编成的十进制小数                 |
| ten2bin()        | 十进制小数                     | 二进制小数                         |
| decode_str()     | 十进制小数和字符的相应概率     | 解码后的字符串                     |

## bmp_huffman.py模块的划分

| 函数名称               | 函数输入                         | 函数输出                             |
| ---------------------- | -------------------------------- | ------------------------------------ |
| Class node             | Huffman结点参数                  | 一个结点                             |
| get_image_list()       | 图像的路径（图像）               | 像素值列表，游程列表，最大二进制长度 |
| get_image_list_count() | 像素值列表                       | 一个字符，频率字典和相应的字符概率   |
| create_nodes()         | 字符串的字符                     | 结点列表                             |
| create_huffman_tree()  | 结点列表                         | Huffman树和根结点                    |
| huffman_encoding()     | 字符频率和Huffman树              | 每个结点被编成的字符串和平均码长     |
| encode_str()           | 像素值列表，结点列表，游程表     | 被编码的字符串                       |
| decode_str()           | 被编码的字符串和结点列表         | 解码后的字符串                       |
| get_H()                | 字符和相应的概率                 | 信源的熵                             |
| get_average_length()   | 游程列表和结点列表               | 平均码长                             |
| compare()              | 图像路径，解码字符串和像素值列表 | 是否解码译码一致                     |

## 界面功能

点击相应的按钮实现相应的功能

![界面](D:\csdn资源包\我上传的\csdn.assets\image-20220718085827102-16581060217751.png)

!(D:\csdn资源包\我上传的\csdn.assets\image-20220718085827102.png)

![图像](D:\csdn资源包\我上传的\csdn.assets\image-20220718085634403.png)	
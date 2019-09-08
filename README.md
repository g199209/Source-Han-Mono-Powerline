## Source-Han-Mono-Powerline

### 背景
对于编程等应用来说，很需要一款美观好看的等宽字体，如果只考虑ASCII字符的话，`Consolas`,  `Source Code Pro` 等都是很好的选择，然而这些字体都是不包含中文的。为了能用一个统一的字体优雅的显示中英文，出现了`YaHei Consolas Hybrid`， `Source Han Mono` 等混合字体。另一方面，`zsh` 等终端扩展软件又使用了 `Powerline` 字符，因此又产生了很多加上 `Powerline` Patch 的字体，如 [powerline/fonts](https://github.com/powerline/fonts) 中这些。然而目前我没找到一款能很好的同时支持中文和 `Powerline` 的字体，所以干脆自己做了一个出来。

此字体基于开源的 [Source Han Mono](https://github.com/adobe-fonts/source-han-mono) 制作得来，使用了 `SourceHanMonoSC` 字体系列。此字体本身就是融合了 `Source Code Pro` & `Source Han Sans (思源黑体)` 得到的，可以较为完美的支持中日韩文字。在原字体基础上的主要改动如下：

1. 加上了7个 `Powerline` 字符的 glyph，具体涉及的字符见[此链接](https://apw-bash-settings.readthedocs.io/en/latest/fontpatching.html)；
2. 由于 ttf/otf 字体格式的限制，包含的 glyph 数不能超过 65535 个，而 `Soucer Han Mono` 中本身就有 65535 个 glyph 了，为了能再加上 `Powerline` glyph，需要删掉一些。因此将其中没有映射到特定 `Unicode` 上的 glyph 全删了，大概删了 2W 多个，目前剩余 4W 多个字符，中文 3W 多个，韩文及日文 1W 多个；
3. 字体中可以根据不同区域设置不同名字，如 `Source Han Mono` 在简体中文环境下的字体名字一般就会显示为 `思源等宽`，然而此特性有时候会带来混乱，部分需要直接填写字体名称的地方到底该填哪个很难确定。因此本字体去掉了区域指定的名称，统一使用 `Source Han Mono Powerline SC` 这一名称。
4. 修改了一些字体元数据信息，应该没有太大的影响。

---------

### 字体特性

1. 同时支持 ASCII 及中日韩文，等宽显示；

2. 支持 `Powerline` 扩展字符；

3. 支持 7 种不同字重，每种字重均包含正体及斜体，当然只有英文字符存在斜体，中文本身就没有斜体的传统，因此正体及斜体我感觉实际上是一样的。具体字重如下：

   | Name       | Font Name                         | Weight |
   | ---------- | --------------------------------- | ------ |
   | Extralight | `Source Han Mono Powerline SC EL` | 250    |
   | Light      | `Source Han Mono Powerline SC L`  | 300    |
   | Normal     | `Source Han Mono Powerline SC N`  | 350    |
   | Regular    | `Source Han Mono Powerline SC`    | 400    |
   | Medium     | `Source Han Mono Powerline SC M`  | 500    |
   | Bold       | `Source Han Mono Powerline SC`    | 700    |
   | Heavy      | `Source Han Mono Powerline SC H`  | 900    |

   `Regular` 和 `Bold` 的字体名称是一样的，字体元数据中有专门配置`Bold`, `Italic` 的地方，`Bold` 及 `Italic` 字体一般是供软件加粗和倾斜使用的，很少单独使用。

-------------------

### 安装使用

考虑到更好的兼容性，生成的字体格式选择了 `ttf`，使用了 `OpenType Layout` & `TrueType Outlines`。

一共 14 个 `ttf` 文件，此外还有个将这些 `ttf` 文件打包到一起的 `ttc` 文件。

实际测试在 Windows 10 上安装此 `ttc` 文件没有什么问题，然而在 Mac 上始终无法装上，不知道是不是文件大小太大了的缘故；而 `Ubuntu` 下需要额外安装软件才能支持 `ttc`。因此除 Windows 外其他平台均建议下载 `ttf` 文件安装使用。

--------

### TODO

此字体我自己使用下来存在以下一些缺陷：

1.  `Source Han Mono` 中英文字宽 `667`，中文字宽 `1000`，期望的效果是3个英文字符对应2个中文字符，然而 `667 * 3` 是不严格等于 `1000 * 2` 的，故两行比较长的中英文夹杂字符并不能很严格的等宽对齐。此问题在 `Source Han Mono` 项目的 Issue 中已经有人提出了，不过好像也没有什么解决办法。
2. `Powerline` glyph 是从 `Source Code for Powerline` 字体中 copy 过来的，已经稍微调整了下图形，不过依然有些对不齐的瑕疵。


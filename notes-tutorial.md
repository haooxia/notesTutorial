# VS Code + Markdown + GitHub 个人知识库搭建教程

- [VS Code + Markdown + GitHub 个人知识库搭建教程](#vs-code--markdown--github-个人知识库搭建教程)
  - [创建仓库 (Optional)](#创建仓库-optional)
  - [常用功能](#常用功能)
    - [预览功能](#预览功能)
    - [插入图片](#插入图片)
    - [导出PDF](#导出pdf)
    - [常用markdown命令](#常用markdown命令)
      - [常用命令](#常用命令)
      - [代码](#代码)
      - [表格](#表格)
      - [公式](#公式)
      - [插件Markdown All in One](#插件markdown-all-in-one)
      - [文件目录添加方法](#文件目录添加方法)
    - [提交到Github](#提交到github)
  - [推荐插件汇总](#推荐插件汇总)

> 数据自主, 通用Markdown格式, 高效编辑, 版本控制

## 创建仓库 (Optional)

> 已有仓库请忽略此步，直接`git clone`到本地然后用vscode打开即可

1. 打开github，创建一个新的repository。如果打算私有，可以设置为Private
![picture 0](images/e94e0dba7229b95fea9131dd9866d637e2a20e51d6b55c6d424fd9127baeb979.png)  

2. `git clone https://github.com/haooxia/notesTutorial.git`
3. 用vscode打开
4. 开始编写内容
5. 提交推送到Github（参考下方`提交到Github`章节）

## 常用功能

### 预览功能

vscode自带markdown预览功能，可以通过`Ctrl+K`松开再按`V`键唤醒双栏预览。

但功能较弱且不够美观吧。

推荐使用`Markdown Preview Enhanced`插件，支持功能不限于自定义风格, 公式, 导出PDF等特性。

快捷键同样是`Ctrl+K`加`V`唤醒右侧预览（效果图如下）。（或者右击markdown编辑界面 -> 点击`Markdown Preview Enhanced: Open Preview to the Side`）

![picture 7](images/1ed7733d3b60a82f4727f3ea7f1307253dbf9b651d387d06745713a63ce7b067.png)  

> 但这俩键很难受，可以考虑自行切换vscode快捷键：`Ctrl+K`加`Ctrl+S`打开快捷键修改面板搜索`preview enhanced side`进行修改，可以使用`Ctrl+Shift+V`。

> 更多功能参考官网：[link](https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-cn/)

### 插入图片

> * 为了整洁，建议将图像存入固定文件夹，而非与markdown文件并列同级目录
> * 所以虽然`Ctrl+V`就可以直接粘贴图片到同级目录下一起上传，但不推荐

**手动方法**：
1. 在项目根目录创建`images`文件夹 (如未创建)
2. 手动复制粘贴图片存入该文件夹
3. 复制**相对路径**并引用
   1. 网络URL则无需下载，直接引用即可加载显示。e.g., `![dojocat](https://octodex.github.com/images/dojocat.jpg)`
4. `git push`的时候把图片和markdown文件都一起提交即可

引用指令: `![图像描述](相对路径)`
![dog](./images/test.jpg)

如需指定图像大小，可利用该HTML格式指令设置图像宽度：`<img src="./images/test.jpg" alt="dog" width="200"/>`

<img src="./images/test.jpg" alt="dog" width="200"/>

---

**全自动方法**:

1. 安装插件`Markdown Image`
2. 右击markdown编辑界面 -> 点击`Paste Image`即可粘贴剪贴板中复制的图像。（或者使用默认快捷键`Shift+Alt+V`）
3. `git push`的时候把图片和markdown文件都一起提交即可

---

详细事项：

1. 按快捷键后该插件会自动在项目根目录下新建一个`images`文件夹（如不存在），然后会把剪切板中的图像粘贴到该文件夹（参见下图），同时自动在markdown中创建图像代码。（**即手动方法的步骤1-3**）
   1. ![picture 1](images/c9917eebbcb574b6e08000ca4b7cf4d01d41e7548daca4ee5bf97d8226302606.png)  
2. 不论你在项目的哪一层级目录的markdown文件中，该插件都只会默认将图像保存到根目录下
3. 首次插入图像可能较慢
4. > 快捷键同样绕手，可以考虑修改为`Ctrl+Shift+I`
5. 如果需要频繁修改图像尺寸，推荐将`markdown-image.base.codeType`从`Markdown`设置为`HTML`格式
6. 更多设置参考官方教程：[link](https://github.com/imlinhanchao/vsc-markdown-image/blob/HEAD/README.zh-cn.md)

### 导出PDF

* 基于插件`Markdown Preview Enhanced`打开预览窗口
* 在pdf上右击鼠标 -> 点击Export -> Chrome(Puppetter) -> PDF
* 打印的pdf会存在当前目录吧

### 常用markdown命令

> markdown常见命令参考网页：[link](https://markdown-it.github.io/)

#### 常用命令

> 对比源码观看

`*`或者`-`用于创建无序列表
`1. `用于创建有序列表
`>`用于引用
`---`用于绘制分割线
`**`用于加粗：**加粗**     
`*`用于斜体：*斜体*  
`~~`用于删除：~~删除线~~
**超链接**快捷创建方式：先复制URL -> 写描述文字 -> 选中描述文字按粘贴键即可形成: `[描述文字](URL)`

**TODO List**创建方式：

- [x] do sth1
- [ ] do sth2
- [ ] ...

#### 代码

单个反引号用于inline code：e.g., `xxx`
三个反引号```用于创建代码块（加上对应边编程语言可以高亮显示，示例如下：
```python
print("hello world")
```

#### 表格

| name | age | city |
|------|------|------|
| xiaoli | 25   | Beijing |
| xiaoming | 30   | Shanghai |

> 有点繁琐，可以让gpt等自动给出markdown格式的表格

#### 公式

行内公式：$f(x)=x^2+2x+1$
单行公式：
$$
f(x) = x^2 + 2x + 1 = (x + 1)^2
$$

多行公式 (支持LaTeX)：
$$
\begin{align}
f(x) &= x^2 + 2x + 1 \\
     &= (x + 1)^2 \\
f'(x) &= \frac{d}{dx}(x^2 + 2x + 1) \\
     &= 2x + 2
\end{align}
$$

#### 插件Markdown All in One

然后推荐下载插件`Markdown All in One`，功能包括但不限于：

* 列表自动添加符号
* Ctrl+B加粗，Ctrl+I斜体
* 自动生成目录

#### 文件目录添加方法

1. 下载插件`Markdown All in One`
2. `Ctrl+Shift+P` -> 输入`toc` -> 选择`Create Table of Contents`即可在相应位置创建


> 注：虽然直接通过指令`[toc]`生成，vscode可以成功渲染，但github界面无法渲染成功（**不推荐**）

### 提交到Github

直接使用vscode可视化工具`commit & push`即可

![picture 6](images/2828400d613411f2f54e6eada618426e5ca26edb76569f0b2095e967ece63e62.png)  

或者命令行:

```shell
git add .
git commit -m "your commit message"
git push origin main
```

## 推荐插件汇总

1. `Markdown Preview Enhanced`: 用于增强markdown预览功能
2. `Markdown Image`: 用于自动插入图片
3. `Markdown All in One`: 用于增强markdown编辑功能
4. `Markdownlint`: 用于markdown语法检查 (如果严格要求语法规范的话)
5. `Word Count CJK`: 用于统计字数


> Author: imxiahao@gmail.com | Date: 2025/7/26

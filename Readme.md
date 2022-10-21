# How to create a ppt using LaTeX
* We can use LaTeX to make a presentation, and it will be a PDF file.
* Beamer
## 基本使用
### 1. 開頭引用
```LaTeX
\documentclass{beamer}
\begin{document}
%%% content %%%
\end{document}
```
### 2. 中文使用與字體指定
```LaTeX
\usepackage{xeCJK}
\setCJKmainfont{微軟正黑體}
```
### 3. 投影片首頁資訊
```LaTeX
\title{Your Title} 
\author{Your Name}
\date{date}

\begin{frame}
\titlepage
\end{frame}
```
* 將title那行改成如下，即可在下方看見標題與頁數
    ```LaTeX
    \title[Your Title\hspace{14em}\insertframenumber/\inserttotalframenumber]
    ```
* Template:
    </br><img src="./img/tmp_page1.png" width="50%" height="50%"/></br>

### 4. 加入投影片與標題
```LaTeX
\begin{frame}
\frametitle{title} %投影片標題
%%% content %%%
\end{frame}
```
* Template:
    </br><img src="./img/tmp_page2.png" width="50%" height="50%"/></br>
### 5. 不顯示提示欄
```LaTeX
\setbeamertemplate{navigation symbols}{}% 隱藏提示欄
```
* Template:
    </br><img src="./img/tmp_page1_nohint.png" width="50%" height="50%"/><img src="./img/tmp_page2_nohint.png" width="50%" height="50%"/></br>
## 主題變換
```LaTeX
\usetheme{ThemeName}
```
### 內建主題  
    |AnnArbor|Dresden |Marburg |
    |:-:|:-:|:-:|
    |Antibes |Frankfurt |Montpellier |
    |Bergen |Goettingen |PaloAlto |
    |Berkeley |Hannover |Pittsburgh |
    |Berlin |Ilmenau |Rochester |
    |Boadilla |JuanLesPins |Singapore |
    |CambridgeUS |Luebeck |Szeged |

### 1. 顏色自定義
```LaTeX
\documentclass[xcolor=svgnames]{beamer}
\usecolortheme[named=LightSlateGrey]{structure}
\setbeamercolor{normal text}{fg=black,bg=AliceBlue}
\usetheme{Warsaw}
```
* 使用xcolor去改變顏色
    * dvipanames
    * svgnames
* Template:
    </br><img src="./img/tmp_page11.png" width="50%" height="50%"/><img src="./img/tmp_page12.png" width="50%" height="50%"/></br>
### 2. 樣式修改  
#### 內主題:
```LaTeX
\useinnertheme{circles}
```
* circles, inmargin, rectangles, rounded 
#### 外主題:
```LaTeX
\useoutertheme{miniframes}
```    
*  infolines, miniframes, shadow, sidebar, smoothbars, smoothtree, split, tree 
* Template:
    * 要加入section才會顯示出名稱
        ```LaTeX
        \section{SectionName}
        ```
    <img src="./img/tmp_page21.png" width="50%" height="50%"/><img src="./img/tmp_page22.png" width="50%" height="50%"/></br>
#### 標記:
```LaTeX
\setbeamertemplate{items}[rectangle]
```
|Name |Description |
|:-:|:-:|
|ball |3D 球形|
|circle |2D 圓形|
|rectangle |2D 方形|
|default |2D 三角|
## 內容控制
### 1.使用`\pause`來分段
```Latex
\section{內容控制}
\begin{frame}
\frametitle{title} %投影片標題
%%% content %%%
因為...
\pause
然後...
\pause
所以...
\end{frame}
```
* Template:
    </br><img src="./img/tmp_page32.png" width="50%" height="50%"/><img src="./img/tmp_page33.png" width="50%" height="50%"/><img src="./img/tmp_page34.png" width="50%" height="50%"/></br>

### 2.條列式也可以用`\pause`暫停
```Latex
\begin{frame}
\frametitle{item+pause} %投影片標題
\begin{itemize}
\item 第一項
\pause
\item 第二項
\pause
\item 第三項
\end{itemize}
\end{frame}
```
* Template:
    </br><img src="./img/tmp_page45.png" width="50%" height="50%"/><img src="./img/tmp_page46.png" width="50%" height="50%"/><img src="./img/tmp_page47.png" width="50%" height="50%"/></br>

### 3.更精確的控制- only vs uncover
#### \only<2->{第二張以後才會出現}
```Latex
\begin{frame}
\frametitle{uncover} %投影片標題
\uncover<2->{第二張以後才會出現uncover}
\begin{itemize}
\item<1-> 第一項
\item<2-> 第二項
\item<3-> 第三項
\end{itemize}
\end{frame}
```
* Template:
    </br><img src="./img/tmp_page58.png" width="50%" height="50%"/><img src="./img/tmp_page59.png" width="50%" height="50%"/><img src="./img/tmp_page510.png" width="50%" height="50%"/></br>

#### \uncover<2->{第二張以後才會出現}
```Latex
\begin{frame}
\frametitle{uncover} %投影片標題
\uncover<2->{第二張以後才會出現uncover}
\begin{itemize}
\item<1-> 第一項
\item<2-> 第二項
\item<3-> 第三項
\end{itemize}
\end{frame}
```
* Template:
    </br><img src="./img/tmp_page511.png" width="50%" height="50%"/><img src="./img/tmp_page512.png" width="50%" height="50%"/><img src="./img/tmp_page513.png" width="50%" height="50%"/></br>
## 文字變化
### 1.標紅重點字
* 使用`\alert`來標紅
```Latex
\section{文字變化}
\begin{frame}
\frametitle{強調文字} %投影片標題
將重點標紅字，在beamer使用\alert{\textbackslash alert}。\\ 
語法:
\textbackslash alert $\lbrace$關鍵字$\rbrace$。\\ 
指定在特定投影片才強調  
\alert<2>{第二張}才重要。  
\end{frame}
```
* Template:
    </br><img src="./img/tmp_page614.png" width="50%" height="50%"/><img src="./img/tmp_page615.png" width="50%" height="50%"/></br>
### 2. 文字顏色
```Latex
\begin{frame}
\frametitle{文字顏色} %投影片標題
將文字以其他顏色顯示，其語法如下:\\
$\lbrace$\textbackslash color $\lbrace$blue$\rbrace$ $\lbrace$藍色的文字$\rbrace$ $\rbrace$\\
效果如下:\\
{\color{blue}{藍色的文字}}\\[10pt]
在特定投影片才變色:\\
只有在{\color<2>{green}{第二張}}才是綠色的。\\
\begin{itemize}
\item 顏色名稱與xcolor的dvipsnames 或svgnames有關。
\end{itemize}
\end{frame}
```
* Template:
    </br><img src="./img/tmp_page716.png" width="50%" height="50%"/><img src="./img/tmp_page717.png" width="50%" height="50%"/></br>
﻿
#  C++ Template 进阶指南

## 0. 前言

###0.1 C++另类简介：比你用的复杂，但比你想的简单

C++似乎从他为世人所知的那天开始便成为天然的话题性编程语言。在它在周围有着形形色色的赞美与贬低之词。当我在微博上透露欲写此文的意愿时，也收到了很多褒贬不一的评论。作为一门语言，能拥有这么多使用并恨着它、使用并畏惧它的用户，也算是语言丛林里的奇观了。

C++之所以变成一门层次丰富、结构多变、语法繁冗的语言，是有着多层次的原因的。Bjarne在《The Design and Evolution of C++》一书中，详细的解释了C++为什么会变成如今（C++98/03）的模样。这本书也是我和陈梓瀚一直对各位已经入门的新手强烈推荐的一本书。通过它你多少可以明白，C++的诸多语法要素之所以变成如今的模样，实属迫不得已。

模板作为C++中最有特色的语言特性，它堪称玄学的语法和语义，理所应当的成为初学者的梦魇。甚至很多工作多年的人也对C++的模板部分保有充分的敬畏。在多数的编码标准中，Template俨然和多重继承一样，成为了一般程序员（非程序库撰写者）的禁区。甚至运用模板较多的Boost的，也成为了“众矢之的”。

但是实际上C++模板远没有想象的那么复杂。我们只需要换一个视角：在C++03的时候，模板本身就可以独立成为一门“语言”。它有“值”，有“函数”，有“表达式”和“语句”。除了语法比较蹩脚外，它既没有指针也没有数组，更没有C++里面复杂的继承和多态。可以说，它要比C语言要简单的多。如果我们把模板当做是一门语言来学习，那只需要花费学习OO零头的时间即可掌握。按照这样的思路，可以说在各种模板书籍中出现的多数技巧，都可以被轻松理解。

简单回顾一下模板的历史。87年的时候，泛型（Generic Programming）变被纳入了C++的考虑范畴，并直接导致了后来模板语法的产生。可以说模板语法一开始就是为了在C++中提供泛型机制。92年的时候，Alexandar Stepanov开始研究利用模板语法制作程序库，后来这一程序库发展成STL，并在93年被接纳入标准中。

此时不少人以为STL已经是C++模板的集大成之作，C++模板技止于此。但是在95年的《C++ Report》上，John Barton和Lee Nackman提出了一个矩阵乘法的模板示例。可以说元编程在那个时候开始被很多人所关注。自此篇文章发表之后，很多人大牛都开始对模板产生了浓厚的兴趣。其中对元编程技法贡献最大的当属Alexandrescu的《Modern C++ Design》及模板程序库Loki。这一2001年发表的图书间接地导致了模板元编程库的出现。书中所使用的Typelist等泛型组件，和Policy等设计方法令人耳目一新。但是因为全书用的是近乎Geek的手法来构造一切设施，因此使得此书阅读起来略有难度。

2002年出版的另一本书《C++ Templates》，可以说是在Template方面的集大成制作。它详细阐述了模板的语法、提供了和模板有关的语言细节信息，举了很多有代表性例子。但是对于模板新手来说，这本书细节如此丰富，让他们随随便便就打了退堂鼓缴械投降。

本文的写作初衷，就是通过“编程语言”的视角，介绍一个简单、清晰的“模板语言”。我会尽可能的将模板的诸多要素连串起来，用一些简单的例子帮助读者学习这门“语言”，让读者在编写、阅读模板代码的时候，能像 `if(exp) { dosomething(); }`一样的信手拈来，让“模板元编程”技术成为读者牢固掌握、可举一反三的有用技能。

###0.2 适宜读者群
C++ Templates和Modern C++ Design的关系

###0.3 版权

## 1. Template的基本语法

###1.1 Template Class的基本语法
###1.2 Template Function的基本语法
###1.3 整型也可是Template参数
###1.4 类中类：灵活的模板定义

## 2.  模板世界的If-Then-Else：特化与偏特化
###2.1 实例化/特化类模板：从类模板到可以定义变量的具体类
###2.2 类模板的匹配规则：特化与部分特化
###2.3 函数模板的重载、特化与部分特化
###2.4 技巧单元：模板与继承

## 3   拿起特化的武器，去写程序吧！
###3.1 利用模板特化规则实现If-Then-Else与Switch-Case
###3.2 特化可以有多个选择：替换失败并不是一个错误，只是一种可能
###3.3 技巧单元：获得类型的属性——类型萃取（Type Traits） 

## 4   用模板写程序吧！骚年！
###4.1 模板上的递归
###4.2 将循环变成递归，将分支变成递归，将一切变成递归
###4.3 实战单元：元编程的Fibonacci数列
###4.4 技巧单元：typename与template的另一种用法
###4.5 实战单元：撰写你自己的元编程“函数”库
###4.6 实战单元：实现元编程上的数据结构——以Vector为例

## 5   关于模板，你还需要知道的其它常识
###5.1 Template-Template Class
###5.2 技巧单元：高阶函数——从函数到函数的组合
###5.3 实战单元：STL中的Allocator Rebinder
###5.4 像看堆栈一样的看出错信息
###5.5 模板的症结：易于实现，难于完美

alexandrescu 关于 min max 的讨论：《再谈Min和Max》

## 6   C++11的新特性
###6.1 变参模板
###6.2 Lambda与模板程序

## 7   结语：讨论有益，争端无用
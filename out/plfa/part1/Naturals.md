---
src       : "src/plfa/part1/Naturals.lagda.md"
title     : "Naturals：自然数"
layout    : page
prev      : /Preface/
permalink : /Naturals/
next      : /Induction/
translators : ["Rongxiao Fu"]
progress  : 100
---

{% raw %}<pre class="Agda"><a id="173" class="Keyword">module</a> <a id="180" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}" class="Module">plfa.part1.Naturals</a> <a id="200" class="Keyword">where</a>
</pre>{% endraw %}
{::comment}
The night sky holds more stars than I can count, though fewer than five
thousand are visible to the naked eye.  The observable universe
contains about seventy sextillion stars.
{:/}

夜空中的星星不计其数，但只有不到五千颗是肉眼可见的。可观测宇宙中则包含大约 7*10^22 颗恒星。

{::comment}
But the number of stars is finite, while natural numbers are infinite.
Count all the stars, and you will still have as many natural numbers
left over as you started with.
{:/}

星星虽多，但却是有限的，而自然数是无限的。就算用自然数把所有的星星都数尽了，剩下的自然数也和开始的一样多。

{::comment}
The naturals are an inductive datatype
{:/}

## 自然数是一种归纳数据类型（Inductive Datatype）

{::comment}
Everyone is familiar with the natural numbers
{:/}

大家都熟悉自然数，例如：

    0
    1
    2
    3
    ...

{::comment}
and so on. We write `ℕ` for the *type* of natural numbers, and say that
`0`, `1`, `2`, `3`, and so on are *values* of type `ℕ`, indicated by
writing `0 : ℕ`, `1 : ℕ`, `2 : ℕ`, `3 : ℕ`, and so on.
{:/}

等等。我们将自然数的**类型（Type）**记作 `ℕ` ，并称 `0`、`1`、`2`、`3` 等数是类型 `ℕ` 的**值（Value）**，表示为 `0 : ℕ`，`1 : ℕ`，`2 : ℕ`，`3 : ℕ` 等等。

{::comment}
The set of natural numbers is infinite, yet we can write down
its definition in just a few lines.  Here is the definition
as a pair of inference rules:
{:/}

自然数集是无限的，然而其定义只需寥寥几行即可写出。下面是用两条
**推导规则（Inference Rules）**定义的自然数：

    --------
    zero : ℕ

    m : ℕ
    ---------
    suc m : ℕ

{::comment}
And here is the definition in Agda:
{:/}

以及用 Agda 定义的自然数：

{% raw %}<pre class="Agda"><a id="1616" class="Keyword">data</a> <a id="ℕ"></a><a id="1621" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1621" class="Datatype">ℕ</a> <a id="1623" class="Symbol">:</a> <a id="1625" class="PrimitiveType">Set</a> <a id="1629" class="Keyword">where</a>
  <a id="ℕ.zero"></a><a id="1637" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1637" class="InductiveConstructor">zero</a> <a id="1642" class="Symbol">:</a> <a id="1644" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a>
  <a id="ℕ.suc"></a><a id="1648" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a>  <a id="1653" class="Symbol">:</a> <a id="1655" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a> <a id="1657" class="Symbol">→</a> <a id="1659" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a>
</pre>{% endraw %}
{::comment}
Here `ℕ` is the name of the *datatype* we are defining,
and `zero` and `suc` (short for *successor*) are the
*constructors* of the datatype.
{:/}

其中 `ℕ` 是我们定义的**数据类型（Datatype）**的名字，而 `zero`（零）和 `suc`
（**后继**，即 **Successor** 的简写）是该数据类型的**构造子（Constructor）**。

{::comment}
Both definitions above tell us the same two things:
{:/}

这两种定义说的是同一件事：

{::comment}
_Base case_: `zero` is a natural number.
_Inductive case_: if `m` is a natural number, then `suc m` is also a
  natural number.
{:/}

* **起始步骤（Base Case）**：`zero` 是一个自然数。
* **归纳步骤（Inductive Case）**：如果 `m` 是一个自然数，那么 `suc m` 也是。

{::comment}
Further, these two rules give the *only* ways of creating natural numbers.
Hence, the possible natural numbers are:
{:/}

此外，这两条规则给出了产生自然数**唯一**的方法。因此，可能的自然数包括：

    zero
    suc zero
    suc (suc zero)
    suc (suc (suc zero))
    ...

{::comment}
We write `0` as shorthand for `zero`; and `1` is shorthand
for `suc zero`, the successor of zero, that is, the natural that comes
after zero; and `2` is shorthand for `suc (suc zero)`, which is the
same as `suc 1`, the successor of one; and `3` is shorthand for the
successor of two; and so on.
{:/}

我们将 `zero` 简写为 `0`；将 `suc zero`，零的后继数，也就是排在零之后的自然数，简写为 `1`；将 `suc (suc zero)`，也就是 `suc 1`，即一的后继数，简写为 `2`；将二的后继数简写为 `3`；以此类推。

{::comment}
#### Exercise `seven` (practice) {#seven}
{:/}

#### 练习 `seven`（实践） {#seven}

{::comment}
Write out `7` in longhand.
{:/}

请写出 `7` 的完整定义。

{::comment}
{% raw %}<pre class="Agda"><a id="3119" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="3156" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}
{::comment}
## Unpacking the inference rules
{:/}

## 推导规则分析

{::comment}
Let's unpack the inference rules.  Each inference rule consists of
zero or more _judgments_ written above a horizontal line, called the
_hypotheses_, and a single judgment written below, called the
_conclusion_.  The first rule is the base case. It has no hypotheses,
and the conclusion asserts that `zero` is a natural.  The second rule
is the inductive case. It has one hypothesis, which assumes that `m`
is a natural, and the conclusion asserts that `suc m`
is a also a natural.
{:/}

我们来分析一下刚才的两条推导规则。每条推导规则包含写在一条水平直线上的零条或多条**判断（Judgment）**，称之为**假设（Hypothesis）**；以及写在直线下的一条判断，称之为**结论（Conclusion）**。第一条规则是起始步骤：它没有任何假设，其结论断言 `zero` 是一个自然数。第二条规则是归纳步骤：它有一条假设，即 `m` 是自然数，而结论断言 `suc m` 也是一个自然数。

{::comment}
Unpacking the Agda definition
{:/}

## Agda 定义分析

{::comment}
Let's unpack the Agda definition. The keyword `data` tells us this is an
inductive definition, that is, that we are defining a new datatype
with constructors.  The phrase
{:/}

现在分析一下 Agda 的定义。关键字 `data` 表示这是一个归纳定义，也就是用构造子定义一个新的数据类型。

    ℕ : Set

{::comment}
tells us that `ℕ` is the name of the new datatype, and that it is a
`Set`, which is the way in Agda of saying that it is a type.  The
keyword `where` separates the declaration of the datatype from the
declaration of its constructors. Each constructor is declared on a
separate line, which is indented to indicate that it belongs to the
corresponding `data` declaration.  The lines
{:/}

表示 `ℕ` 是新的数据类型的名字，它是一个 `Set`，也就是在 Agda 中对类型的称呼。关键字 `where` 用于分隔数据类型的声明和构造子的声明。每个构造子的声明独占一行，用缩进来指明它所属的 `data` 声明。

    zero : ℕ
    suc  : ℕ → ℕ

{::comment}
give _signatures_ specifying the types of the constructors `zero` and `suc`.
They tell us that `zero` is a natural number and that `suc` takes a natural
number as argument and returns a natural number.
{:/}

这两行给出了构造子 `zero` 和 `suc` 的类型**签名（Signature）**。它们表示 `zero` 是一个自然数，`suc` 则取一个自然数作为参数，返回另一个自然数。

{::comment}
You may have noticed that `ℕ` and `→` don't appear on your keyboard.
They are symbols in _unicode_.  At the end of each chapter is a list
of all unicode symbols introduced in the chapter, including
instructions on how to type them in the Emacs text editor.  Here
_type_ refers to typing with fingers as opposed to data types!
{:/}

读者可能注意到 `ℕ` 和 `→` 在键盘上没有对应的按键。它们是
**Unicode（统一码）**中的符号。每一章的结尾都会有本章节引入的 Unicode
符号列表，以及在 Emacs 编辑器中输入它们的方法。

{::comment}
The story of creation
{:/}

## 创世故事

{::comment}
Let's look again at the rules that define the natural numbers:
{:/}

我们再看一下自然数的定义规则：

{::comment}
_Base case_: `zero` is a natural number.
_Inductive case_: if `m` is a natural number, then `suc m` is also a
  natural number.
{:/}

* **起始步骤（Base Case）**：`zero` 是一个自然数。
* **归纳步骤（Inductive Case）**：如果 `m` 是一个自然数，那么 `suc m` 也是。

{::comment}
Hold on! The second line defines natural numbers in terms of natural
numbers. How can that possibly be allowed?  Isn't this as useless a
definition as "Brexit means Brexit"?
{:/}

等等！第二行用自然数定义了自然数，这怎么能行？这个定义难道不会像「脱欧即是脱欧」一样无用吗？

【译注：「脱欧即是脱欧」是英国首相特蕾莎·梅提出的一句口号。】

{::comment}
In fact, it is possible to assign our definition a meaning without
resorting to unpermitted circularities.  Furthermore, we can do so
while only working with _finite_ sets and never referring to the
_infinite_ set of natural numbers.
{:/}

实际上，不必通过自我指涉，我们的自然数定义也是可以被赋予意义的。我们甚至只需要处理**有限**的集合，而不必涉及**无限**的自然数集。

{::comment}
We will think of it as a creation story.  To start with, we know about
no natural numbers at all:
{:/}

我们可以将这个过程比作一个创世故事。起初，我们对自然数一无所知：

{::comment}
    -- In the beginning, there are no natural numbers.
{:/}

    -- 起初，世上没有自然数。

{::comment}
Now, we apply the rules to all the natural numbers we know about.  The
base case tells us that `zero` is a natural number, so we add it to the set
of known natural numbers.  The inductive case tells us that if `m` is a
natural number (on the day before today) then `suc m` is also a
natural number (today).  We didn't know about any natural numbers
before today, so the inductive case doesn't apply:
{:/}

现在，我们对所有已知的自然数应用之前的规则。起始步骤告诉我们 `zero` 是一个自然数，所以我们将它加入已知自然数的集合中。归纳步骤告诉我们如果
「昨天的」`m` 是一个自然数，那么「今天的」`suc m` 也是一个自然数。我们在今天之前并不知道任何自然数，所以归纳步骤在此处不适用。

{::comment}
    -- On the first day, there is one natural number.
    zero : ℕ
{:/}

    -- 第一天，世上有了一个自然数。
    zero : ℕ

{::comment}
Then we repeat the process. On the next day we know about all the
numbers from the day before, plus any numbers added by the rules.  The
base case tells us that `zero` is a natural number, but we already knew
that. But now the inductive case tells us that since `zero` was a natural
number yesterday, then `suc zero` is a natural number today:
{:/}

然后我们重复此过程。今天我们知道昨天的所有自然数，以及任何通过规则添加的数。起始步骤依然告诉我们 `zero` 是一个自然数，我们已经知道这件事了。而如今归纳步骤告诉我们，由于 `zero` 在昨天是自然数，那么 `suc zero` 在今天也是自然数：

{::comment}
    -- On the second day, there are two natural numbers.
    zero : ℕ
    suc zero : ℕ
{:/}

    -- 第二天，世上有了两个自然数。
    zero : ℕ
    suc zero : ℕ

{::comment}
And we repeat the process again. Now the inductive case
tells us that since `zero` and `suc zero` are both natural numbers, then
`suc zero` and `suc (suc zero)` are natural numbers. We already knew about
the first of these, but the second is new:
{:/}

我们再次重复此过程。现在归纳步骤告诉我们，由于 `zero` 和 `suc zero` 都是自然数，因此 `suc zero` 和 `suc (suc zero)` 也是自然数。我们已经知道 `suc zero`
是自然数了，而后者 `suc (suc zero)` 是新加入的。

{::comment}
    -- On the third day, there are three natural numbers.
    zero : ℕ
    suc zero : ℕ
    suc (suc zero) : ℕ
{:/}

    -- 第三天，世上有了三个自然数。
    zero : ℕ
    suc zero : ℕ
    suc (suc zero) : ℕ

{::comment}
You've got the hang of it by now:
{:/}

此时规律已经很明显了。

{::comment}
    -- On the fourth day, there are four natural numbers.
    zero : ℕ
    suc zero : ℕ
    suc (suc zero) : ℕ
    suc (suc (suc zero)) : ℕ
{:/}

    -- 第四天，世上有了四个自然数。
    zero : ℕ
    suc zero : ℕ
    suc (suc zero) : ℕ
    suc (suc (suc zero)) : ℕ

{::comment}
The process continues.  On the _n_'th day there will be _n_ distinct
natural numbers. Every natural number will appear on some given day.
In particular, the number _n_ first appears on day _n+1_. And we
never actually define the set of numbers in terms of itself. Instead,
we define the set of numbers on day _n+1_ in terms of the set of
numbers on day _n_.
{:/}

此过程可以继续下去。在第 *n* 天会有 *n* 个不同的自然数。每个自然数都会在某一天出现。具体来说，自然数 *n* 在第 *n+1* 天首次出现。至此，我们并没有使用自然数集来定义其自身，而是根据第 *n* 天的数集定义了第 *n+1* 天的数集。

{::comment}
A process like this one is called _inductive_. We start with nothing, and
build up a potentially infinite set by applying rules that convert one
finite set into another finite set.
{:/}

像这样的过程被称作是**归纳的（Inductive）**。我们从一无所有开始，通过应用将一个有限集合转换到另一个有限集合的规则，逐步生成潜在无限的集合。

{::comment}
The rule defining zero is called a _base case_, because it introduces
a natural number even when we know no other natural numbers.  The rule
defining successor is called an _inductive case_, because it
introduces more natural numbers once we already know some.  Note the
crucial role of the base case.  If we only had inductive rules, then
we would have no numbers in the beginning, and still no numbers on the
second day, and on the third, and so on.  An inductive definition lacking
a base case is useless, as in the phrase "Brexit means Brexit".
{:/}

定义了零的规则之所以被称作**起始步骤**，是因为它在我们还不知道其它自然数时就引入了一个自然数。定义了后继数的规则之所以被称作**归纳步骤**，则是因为它在已知自然数的基础上引入了更多自然数。其中，起始步骤的重要性不可小觑。如果只有归纳步骤，那么第一天就没有任何自然数。第二天，第三天，无论多久也依旧没有。一个没有起始步骤的归纳定义是无用的，就像「脱欧即是脱欧」一样。

{::comment}
Philosophy and history
{:/}

## 哲学和历史

{::comment}
A philosopher might observe that our reference to the first day,
second day, and so on, implicitly involves an understanding of natural
numbers.  In this sense, our definition might indeed be regarded as in
some sense circular, but we need not let this disturb us.
Everyone possesses a good informal understanding of the natural
numbers, which we may take as a foundation for their formal
description.
{:/}

哲学家发现，我们对「第一天」「第二天」等说法的使用暗含了对自然数的理解。在这个层面上，我们对自然数的定义也许某种程度上可以说是循环的，但我们不必为此烦恼。每个人对自然数都有良好的非形式化的理解，而我们可以将它作为形式化描述自然数的基础。

{::comment}
While the natural numbers have been understood for as long as people
can count, the inductive definition of the natural numbers is relatively
recent.  It can be traced back to Richard Dedekind's paper "_Was sind
und was sollen die Zahlen?_" (What are and what should be the
numbers?), published in 1888, and Giuseppe Peano's book "_Arithmetices
principia, nova methodo exposita_" (The principles of arithmetic
presented by a new method), published the following year.
{:/}

尽管从人类开始计数起，自然数就被人所认知，然而其归纳定义却是近代的事情。这可以追溯到理查德·戴德金（Richard Dedekind）于 1888 年发表的论文
*Was sind und was sollen die Zahlen?*"（《数是什么，应该是什么？》），以及朱塞佩·皮亚诺（Giuseppe Peano）于次年发表的著作
"*Arithmetices principia, nova methodo exposita*"（《算术原理：用一种新方法呈现》）。

{::comment}
A pragma
{:/}

## 编译指令

{::comment}
In Agda, any text following `--` or enclosed between `{-`
and `-}` is considered a _comment_.  Comments have no effect on the
code, with the exception of one special kind of comment, called a
_pragma_, which is enclosed between `{-#` and `#-}`.
{:/}

在 Agda 中，任何跟在 `--` 之后或者由 `{-` 和 `-}` 包裹的文字都会被视为
**注释（Comment）**。一般的注释对代码没有任何作用，但有一种例外，这种注释被称作**编译指令（Pragma）**，由 `{-#` 和 `#-}` 包裹。

{::comment}
Including the line
{:/}

{% raw %}<pre class="Agda"><a id="12421" class="Symbol">{-#</a> <a id="12425" class="Keyword">BUILTIN</a> <a id="12433" class="Pragma">NATURAL</a> <a id="12441" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1621" class="Datatype">ℕ</a> <a id="12443" class="Symbol">#-}</a>
</pre>{% endraw %}
{::comment}
tells Agda that `ℕ` corresponds to the natural numbers, and hence one
is permitted to type `0` as shorthand for `zero`, `1` as shorthand for
`suc zero`, `2` as shorthand for `suc (suc zero)`, and so on.  The
declaration is not permitted unless the type given has exactly two
constructors, one with no arguments (corresponding to zero) and
one with a single argument of the same type given in the pragma
(corresponding to successor).
{:/}

这一行告诉 Agda 数据类型 `ℕ` 对应了自然数，然后编写者就可以将 `zero` 简写为 `0`，将 `suc zero` 简写为 `1`，将 `suc (suc zero)` 简写为 `2` 了，以此类推。只有在给出的数据类型有且只有两个构造子，其中一个没有参数（对应零），另一个仅取一个和被定义的数据类型一样的参数（对应后继数）的时候，这条声明才是合乎规定的。

{::comment}
As well as enabling the above shorthand, the pragma also enables a
more efficient internal representation of naturals using the Haskell
type for arbitrary-precision integers.  Representing the natural _n_
with `zero` and `suc` requires space proportional to _n_, whereas
representing it as an arbitrary-precision integer in Haskell only
requires space proportional to the logarithm of _n_.
{:/}

在启用上述简写的同时，这条编译指令也会用 Haskell 的任意精度整数类型来提供更高效的自然数内部表示。用 `zero` 和 `suc` 表示自然数 *n* 要占用正比于 *n* 的空间，而将其表示为 Haskell 中的任意精度整数只会占用正比于 *n* 的对数的空间。

{::comment}
Imports
{:/}

## 导入模块

{::comment}
Shortly we will want to write some equations that hold between
terms involving natural numbers.  To support doing so, we import
the definition of equality and notations for reasoning
about it from the Agda standard library:
{:/}

我们很快就能写一些包含自然数的等式了。在此之前，我们需要从 Agda 标准库中导入**相等性（Equality）**的定义和用于等式推理的记法：

{% raw %}<pre class="Agda"><a id="13999" class="Keyword">import</a> <a id="14006" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.html" class="Module">Relation.Binary.PropositionalEquality</a> <a id="14044" class="Symbol">as</a> <a id="14047" class="Module">Eq</a>
<a id="14050" class="Keyword">open</a> <a id="14055" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.html" class="Module">Eq</a> <a id="14058" class="Keyword">using</a> <a id="14064" class="Symbol">(</a><a id="14065" href="Agda.Builtin.Equality.html#125" class="Datatype Operator">_≡_</a><a id="14068" class="Symbol">;</a> <a id="14070" href="Agda.Builtin.Equality.html#182" class="InductiveConstructor">refl</a><a id="14074" class="Symbol">)</a>
<a id="14076" class="Keyword">open</a> <a id="14081" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2499" class="Module">Eq.≡-Reasoning</a> <a id="14096" class="Keyword">using</a> <a id="14102" class="Symbol">(</a><a id="14103" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2597" class="Function Operator">begin_</a><a id="14109" class="Symbol">;</a> <a id="14111" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">_≡⟨⟩_</a><a id="14116" class="Symbol">;</a> <a id="14118" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2892" class="Function Operator">_∎</a><a id="14120" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
The first line brings the standard library module that defines
equality into scope and gives it the name `Eq`. The second line
opens that module, that is, adds all the names specified in the
`using` clause into the current scope. In this case the names added
are `_≡_`, the equality operator, and `refl`, the name for evidence
that two terms are equal.  The third line takes a module that
specifies operators to support reasoning about equivalence, and adds
all the names specified in the `using` clause into the current scope.
In this case, the names added are `begin_`, `_≡⟨⟩_`, and `_∎`.  We
will see how these are used below.  We take these as givens for now,
but will see how they are defined in
Chapter [Equality]({{ site.baseurl }}/Equality/).
{:/}

第一行代码将标准库中定义了相等性的模块导入到当前**作用域（Scope）**中，并将其命名为 `Eq`。第二行打开了这个模块，也就是将所有在 `using`
从句中指定的名称添加到当前作用域中。此处添加的名称有相等性运算符 `_≡_`
和两个项相等的证据 `refl`。第三行选取的模块提供了用于等价关系推理的运算符，并将
`using` 从句中指定的名称添加到当前作用域。此处添加的名称有 `begin_`、
`_≡⟨⟩_` 和 `_∎`。我们后面会看到这些运算符的使用方法。现在暂且把它们当作现成的工具来使用，不深究其细节。但我们会在[相等性]({{ site.baseurl }}/Equality/)一章中学习它们的具体定义。

{::comment}
Agda uses underbars to indicate where terms appear in infix or mixfix
operators. Thus, `_≡_` and `_≡⟨⟩_` are infix (each operator is written
between two terms), while `begin_` is prefix (it is written before a
term), and `_∎` is postfix (it is written after a term).
{:/}

Agda 用下划线来标注**项（Term）**在中缀（Infix）或混缀（Mixfix）运算符中项出现的位置。因此，`_≡_` 和 `_≡⟨⟩_` 是中缀的（运算符写在两个项之间），而 `begin_` 是前缀的
（运算符写在项之前），`_∎` 则是后缀的（运算符写在项之后）。

{::comment}
Parentheses and semicolons are among the few characters that cannot
appear in names, so we do not need extra spaces in the `using` list.
{:/}

括号和分号是少有的几个不能在名称中出现的的字符，于是我们在 `using`
列表中不需要额外的空格来消除歧义。

{::comment}
Operations on naturals are recursive functions {#plus}
{:/}

## 自然数的运算是递归函数 {#plus}

{::comment}
Now that we have the natural numbers, what can we do with them?
For instance, can we define arithmetic operations such as
addition and multiplication?
{:/}

既然我们有了自然数，那么可以用它们做什么呢？比如，我们能定义加法和乘法之类的算术运算吗？

{::comment}
As a child I spent much time memorising tables of addition and
multiplication.  At first the rules seemed tricky and I would often
make mistakes.  It came as a shock to me to discover _recursion_,
a simple technique by which every one of the infinite possible
instances of addition and multiplication can be specified in
just a couple of lines.
{:/}

我儿时曾花费了大量的时间来记忆加法表和乘法表。最开始，运算规则看起来很复杂，我也经常犯错。在发现**递归（Recursion）**时，我如同醍醐灌顶。有了这种简单的技巧，无数的加法和乘法运算只用几行就能概括。

{::comment}
Here is the definition of addition in Agda:
{:/}

这是用 Agda 编写的加法定义：

{% raw %}<pre class="Agda"><a id="_+_"></a><a id="16726" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#16726" class="Function Operator">_+_</a> <a id="16730" class="Symbol">:</a> <a id="16732" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a> <a id="16734" class="Symbol">→</a> <a id="16736" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a> <a id="16738" class="Symbol">→</a> <a id="16740" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a>
<a id="16742" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1637" class="InductiveConstructor">zero</a> <a id="16747" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="16749" href="plfa.part1.Naturals.html#16749" class="Bound">n</a> <a id="16751" class="Symbol">=</a> <a id="16753" href="plfa.part1.Naturals.html#16749" class="Bound">n</a>
<a id="16755" class="Symbol">(</a><a id="16756" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a> <a id="16760" href="plfa.part1.Naturals.html#16760" class="Bound">m</a><a id="16761" class="Symbol">)</a> <a id="16763" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="16765" href="plfa.part1.Naturals.html#16765" class="Bound">n</a> <a id="16767" class="Symbol">=</a> <a id="16769" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="16773" class="Symbol">(</a><a id="16774" href="plfa.part1.Naturals.html#16760" class="Bound">m</a> <a id="16776" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="16778" href="plfa.part1.Naturals.html#16765" class="Bound">n</a><a id="16779" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
Let's unpack this definition.  Addition is an infix operator.  It is
written with underbars where the arguments go, hence its name is
`_+_`.  The first line is a signature specifying the type of the operator.
The type `ℕ → ℕ → ℕ`, indicates that addition accepts two naturals
and returns a natural.  Infix notation is just a shorthand for application;
the terms `m + n` and `_+_ m n` are equivalent.
{:/}

我们来分析一下它的定义。加法是一种中缀运算符，其名为 `_+_`，其中参数的位置用下划线表示。第一行指定了运算符的类型签名。类型 `ℕ → ℕ → ℕ` 表示加法接受两个自然数作为参数，并返回一个自然数。中缀记法只是函数应用的简写，
`m + n` 和 `_+_ m n` 这两个项是等价的。

{::comment}
The definition has a base case and an inductive case, corresponding to
those for the natural numbers.  The base case says that adding zero to
a number, `zero + n`, returns that number, `n`.  The inductive case
says that adding the successor of a number to another number,
`(suc m) + n`, returns the successor of adding the two numbers, `suc (m + n)`.
We say we use _pattern matching_ when constructors appear on the
left-hand side of an equation.
{:/}

它的定义包含一个起始步骤和一个归纳步骤，与自然数的定义对应。起始步骤说明零加上一个数仍返回这个数，即 `zero + n` 等于 `n`。归纳步骤说明一个数的后继数加上另一个数返回两数之和的后继数，即 `(suc m) + n` 等于 `suc (m + n)`。在加法的定义中，构造子出现在了等式左边，我们称之为**模式匹配（Pattern Matching）**。

{::comment}
If we write `zero` as `0` and `suc m` as `1 + m`, the definition turns
into two familiar equations:
{:/}

如果我们将 `zero` 写作 `0`，将 `suc m` 写作 `1 + m`，上面的定义就变成了两个熟悉的等式。

     0       + n  ≡  n
     (1 + m) + n  ≡  1 + (m + n)

{::comment}
The first follows because zero is an identity for addition, and the
second because addition is associative.  In its most general form,
associativity is written
{:/}

因为零是加法的幺元，所以第一个等式成立。又因为加法满足结合律，所以第二个等式也成立。加法结合律的一般形式如下，说明运算结果与括号位置无关。

     (m + n) + p  ≡  m + (n + p)

{::comment}
meaning that the location of parentheses is irrelevant.  We get the
second equation from the third by taking `m` to be `1`, `n` to be `m`,
and `p` to be `n`.  We write `=` for definitions, while we
write `≡` for assertions that two already defined things are the same.
{:/}

将上面第三个等式中的 `m` 换成 `1`，`n` 换成 `m`，`p` 换成 `n`，我们就得到了第二个等式。我们用等号 `=` 表示定义，用 `≡` 断言两个已定义的事物相等。

{::comment}
The definition is _recursive_, in that the last line defines addition
in terms of addition.  As with the inductive definition of the
naturals, the apparent circularity is not a problem.  It works because
addition of larger numbers is defined in terms of addition of smaller
numbers.  Such a definition is called _well founded_.
{:/}

加法的定义是**递归（Recursive）**的，因为在最后一行我们用加法定义了加法。与自然数的归纳定义类似，这种表面上的循环性并不会造成问题，因为较大的数相加是用较小的数相加定义的。这样的定义被称作是**良基的（Well founded）**。

{::comment}
For example, let's add two and three:
{:/}

例如，我们来计算二加三：

{% raw %}<pre class="Agda"><a id="19455" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#19455" class="Function">_</a> <a id="19457" class="Symbol">:</a> <a id="19459" class="Number">2</a> <a id="19461" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="19463" class="Number">3</a> <a id="19465" href="Agda.Builtin.Equality.html#125" class="Datatype Operator">≡</a> <a id="19467" class="Number">5</a>
<a id="19469" class="Symbol">_</a> <a id="19471" class="Symbol">=</a>
  <a id="19475" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2597" class="Function Operator">begin</a>
    <a id="19485" class="Number">2</a> <a id="19487" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#16726" class="Function Operator">+</a> <a id="19489" class="Number">3</a>
  <a id="19493" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>    <a id="19500" class="Comment">-- 展开为</a>
    <a id="19511" class="Symbol">(</a><a id="19512" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a> <a id="19516" class="Symbol">(</a><a id="19517" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19521" href="plfa.part1.Naturals.html#1637" class="InductiveConstructor">zero</a><a id="19525" class="Symbol">))</a> <a id="19528" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="19530" class="Symbol">(</a><a id="19531" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19535" class="Symbol">(</a><a id="19536" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19540" class="Symbol">(</a><a id="19541" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19545" href="plfa.part1.Naturals.html#1637" class="InductiveConstructor">zero</a><a id="19549" class="Symbol">)))</a>
  <a id="19555" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>    <a id="19562" class="Comment">-- 归纳步骤</a>
    <a id="19574" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a> <a id="19578" class="Symbol">((</a><a id="19580" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19584" href="plfa.part1.Naturals.html#1637" class="InductiveConstructor">zero</a><a id="19588" class="Symbol">)</a> <a id="19590" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="19592" class="Symbol">(</a><a id="19593" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19597" class="Symbol">(</a><a id="19598" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19602" class="Symbol">(</a><a id="19603" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19607" href="plfa.part1.Naturals.html#1637" class="InductiveConstructor">zero</a><a id="19611" class="Symbol">))))</a>
  <a id="19618" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>    <a id="19625" class="Comment">-- 归纳步骤</a>
    <a id="19637" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a> <a id="19641" class="Symbol">(</a><a id="19642" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19646" class="Symbol">(</a><a id="19647" href="plfa.part1.Naturals.html#1637" class="InductiveConstructor">zero</a> <a id="19652" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="19654" class="Symbol">(</a><a id="19655" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19659" class="Symbol">(</a><a id="19660" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19664" class="Symbol">(</a><a id="19665" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19669" href="plfa.part1.Naturals.html#1637" class="InductiveConstructor">zero</a><a id="19673" class="Symbol">)))))</a>
  <a id="19681" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>    <a id="19688" class="Comment">-- 起始步骤</a>
    <a id="19700" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a> <a id="19704" class="Symbol">(</a><a id="19705" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19709" class="Symbol">(</a><a id="19710" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19714" class="Symbol">(</a><a id="19715" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19719" class="Symbol">(</a><a id="19720" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19724" href="plfa.part1.Naturals.html#1637" class="InductiveConstructor">zero</a><a id="19728" class="Symbol">))))</a>
  <a id="19735" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>    <a id="19742" class="Comment">-- 简写为</a>
    <a id="19753" class="Number">5</a>
  <a id="19757" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2892" class="Function Operator">∎</a>
</pre>{% endraw %}
{::comment}
We can write the same derivation more compactly by only
expanding shorthand as needed:
{:/}

我们可以按需展开简写，把同样的推导过程写得更加紧凑。

{% raw %}<pre class="Agda"><a id="19901" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#19901" class="Function">_</a> <a id="19903" class="Symbol">:</a> <a id="19905" class="Number">2</a> <a id="19907" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="19909" class="Number">3</a> <a id="19911" href="Agda.Builtin.Equality.html#125" class="Datatype Operator">≡</a> <a id="19913" class="Number">5</a>
<a id="19915" class="Symbol">_</a> <a id="19917" class="Symbol">=</a>
  <a id="19921" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2597" class="Function Operator">begin</a>
    <a id="19931" class="Number">2</a> <a id="19933" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#16726" class="Function Operator">+</a> <a id="19935" class="Number">3</a>
  <a id="19939" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>
    <a id="19947" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a> <a id="19951" class="Symbol">(</a><a id="19952" class="Number">1</a> <a id="19954" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="19956" class="Number">3</a><a id="19957" class="Symbol">)</a>
  <a id="19961" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>
    <a id="19969" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a> <a id="19973" class="Symbol">(</a><a id="19974" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="19978" class="Symbol">(</a><a id="19979" class="Number">0</a> <a id="19981" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="19983" class="Number">3</a><a id="19984" class="Symbol">))</a>
  <a id="19989" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>
    <a id="19997" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a> <a id="20001" class="Symbol">(</a><a id="20002" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="20006" class="Number">3</a><a id="20007" class="Symbol">)</a>
  <a id="20011" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>
    <a id="20019" class="Number">5</a>
  <a id="20023" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2892" class="Function Operator">∎</a>
</pre>{% endraw %}
{::comment}
The first line matches the inductive case by taking `m = 1` and `n = 3`,
the second line matches the inductive case by taking `m = 0` and `n = 3`,
and the third line matches the base case by taking `n = 3`.
{:/}

第一行取 `m = 1` 和 `n = 3` 匹配了归纳步骤，第二行取
`m = 0` 和 `n = 3` 匹配了归纳步骤，第三行取 `n = 3` 匹配了起始步骤。

{::comment}
Both derivations consist of a signature (written with a colon, `:`),
giving a type, and a binding (written with an equal sign, `=`),
giving a term of the given type.  Here we use the dummy name `_`.  The
dummy name can be reused, and is convenient for examples.  Names other
than `_` must be used only once in a module.
{:/}

以上两个推导过程都由一个类型签名（包含冒号 `:` 的一行）和一个提供对应类型的项的绑定（Binding）（包含等号 `=` 的一行及之后的部分）组成。在编写代码时我们用了虚设名称 `_`。虚设名称可以被重复使用，在举例时非常方便。除了 `_` 之外的名称在一个模块里只能被定义一次。

{::comment}
Here the type is `2 + 3 ≡ 5` and the term provides _evidence_ for the
corresponding equation, here written in tabular form as a chain of
equations.  The chain starts with `begin` and finishes with `∎`
(pronounced "qed" or "tombstone", the latter from its appearance), and
consists of a series of terms separated by `≡⟨⟩`.
{:/}

这里的类型是 `2 + 3 ≡ 5`，而该等式写成列表形式的等式链的项，提供了类型中表示等式成立的**证据（Evidence）**。该等式链由 `begin` 开始，以 `∎` 结束（`∎`
可读作「qed（证毕）」或「tombstone（墓碑符号）」，后者来自于其外观），并由一系列 `≡⟨⟩` 分隔的项组成。

{::comment}
In fact, both proofs are longer than need be, and Agda is satisfied
with the following:
{:/}

其实，以上两种证明都比实际所需的要长，下面的证明就足以让 Agda 满意了。

{% raw %}<pre class="Agda"><a id="21475" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#21475" class="Function">_</a> <a id="21477" class="Symbol">:</a> <a id="21479" class="Number">2</a> <a id="21481" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="21483" class="Number">3</a> <a id="21485" href="Agda.Builtin.Equality.html#125" class="Datatype Operator">≡</a> <a id="21487" class="Number">5</a>
<a id="21489" class="Symbol">_</a> <a id="21491" class="Symbol">=</a> <a id="21493" href="Agda.Builtin.Equality.html#182" class="InductiveConstructor">refl</a>
</pre>{% endraw %}
{::comment}
Agda knows how to compute the value of `2 + 3`, and so can immediately
check it is the same as `5`.  A binary relation is said to be _reflexive_
if every value relates to itself.  Evidence that a value is equal to
itself is written `refl`.
{:/}

Agda 知道如何计算 `2 + 3` 的值，也可以立刻确定这个值和 `5` 是一样的。如果一个二元关系（Binary Relation）中每个值都和自己相关，我们称这个二元关系满足
**自反性（Reflexivity）**。在 Agda 中，一个值等于其自身的证据写作 `refl`。

{::comment}
In the chains of equations, all Agda checks is that each term
simplifies to the same value. If we jumble the equations, omit lines, or
add extraneous lines it will still be accepted.  It's up to us to write
the equations in an order that makes sense to the reader.
{:/}

在等式链中，Agda 只检查每个项是否都能化简为相同的值。如果我们打乱等式顺序，省略或者加入一些额外的步骤，证明仍然会被接受。我们需要自己来保证等式的顺序便于理解。

{::comment}
Here `2 + 3 ≡ 5` is a type, and the chains of equations (and also
`refl`) are terms of the given type; alternatively, one can think of
each term as _evidence_ for the assertion `2 + 3 ≡ 5`.  This duality
of interpretation---of a type as a proposition, and of a term as
evidence---is central to how we formalise concepts in Agda, and will
be a running theme throughout this book.
{:/}

在这里，`2 + 3 ≡ 5` 是一个类型，等式链（以及 `refl`）都是这个类型的项。换言之，我们也可以把每个项都看作断言 `2 + 3 ≡ 5` 的**证据**。这种解释的对偶性——类型即命题，项即证据——是我们在 Agda 中形式化各种概念的核心，也是贯穿本书的主题。

{::comment}
Note that when we use the word _evidence_ it is nothing equivocal.  It
is not like testimony in a court which must be weighed to determine
whether the witness is trustworthy.  Rather, it is ironclad.  The
other word for evidence, which we will use interchangeably, is _proof_.
{:/}

注意，当我们使用**证据**这个词时不容一点含糊。这里的证据确凿不移，不像法庭上的证词一样必须被反复权衡以决定证人是否可信。我们也会使用**证明**一词表达相同的意思，在本书中这两个词可以互换使用。

{::comment}
#### Exercise `+-example` (practice) {#plus-example}
{:/}

#### 练习 `+-example`（实践） {#plus-example}

{::comment}
Compute `3 + 4`, writing out your reasoning as a chain of equations.
{:/}

计算 `3 + 4`，将你的推导过程写成等式链。

{::comment}
{% raw %}<pre class="Agda"><a id="23455" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="23492" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}
{::comment}
Multiplication
{:/}

## 乘法

{::comment}
Once we have defined addition, we can define multiplication
as repeated addition:
{:/}

一旦我们定义了加法，我们就可以将乘法定义为重复的加法。

{% raw %}<pre class="Agda"><a id="_*_"></a><a id="23683" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#23683" class="Function Operator">_*_</a> <a id="23687" class="Symbol">:</a> <a id="23689" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a> <a id="23691" class="Symbol">→</a> <a id="23693" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a> <a id="23695" class="Symbol">→</a> <a id="23697" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a>
<a id="23699" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1637" class="InductiveConstructor">zero</a>    <a id="23707" href="plfa.part1.Naturals.html#23683" class="Function Operator">*</a> <a id="23709" href="plfa.part1.Naturals.html#23709" class="Bound">n</a>  <a id="23712" class="Symbol">=</a>  <a id="23715" href="plfa.part1.Naturals.html#1637" class="InductiveConstructor">zero</a>
<a id="23720" class="Symbol">(</a><a id="23721" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a> <a id="23725" href="plfa.part1.Naturals.html#23725" class="Bound">m</a><a id="23726" class="Symbol">)</a> <a id="23728" href="plfa.part1.Naturals.html#23683" class="Function Operator">*</a> <a id="23730" href="plfa.part1.Naturals.html#23730" class="Bound">n</a>  <a id="23733" class="Symbol">=</a>  <a id="23736" href="plfa.part1.Naturals.html#23730" class="Bound">n</a> <a id="23738" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="23740" class="Symbol">(</a><a id="23741" href="plfa.part1.Naturals.html#23725" class="Bound">m</a> <a id="23743" href="plfa.part1.Naturals.html#23683" class="Function Operator">*</a> <a id="23745" href="plfa.part1.Naturals.html#23730" class="Bound">n</a><a id="23746" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
Computing `m * n` returns the sum of `m` copies of `n`.
{:/}

计算 `m * n` 返回的结果是 `m` 个 `n` 之和。

{::comment}
Again, rewriting turns the definition into two familiar equations:
{:/}

重写定义再一次给出了两个熟悉的等式：

    0       * n  ≡  0
    (1 + m) * n  ≡  n + (m * n)

{::comment}
The first follows because zero times anything is zero, and the second
follows because multiplication distributes over addition.
In its most general form, distribution of multiplication over addition
is written
{:/}

因为零乘任何数都是零，所以第一个等式成立。因为乘法对加法有分配律，所以第二个等式也成立。乘法对加法的分配律的一般形式如下：

    (m + n) * p  ≡  (m * p) + (n * p)

{::comment}
We get the second equation from the third by taking `m` to be `1`, `n`
to be `m`, and `p` to be `n`, and then using the fact that one is an
identity for multiplication, so `1 * n ≡ n`.
{:/}

将上面第三个等式中的 `m` 换成 `1`，`n` 换成 `m`，`p` 换成 `n`，再根据一是乘法的幺元，也就是 `1 * n ≡ n`，我们就得到了第二个等式。

{::comment}
Again, the definition is well founded in that multiplication of
larger numbers is defined in terms of multiplication of smaller numbers.
{:/}

这个定义也是良基的，因为较大的数相乘是用较小的数相乘定义的。

{::comment}
For example, let's multiply two and three:
{:/}

例如，我们来计算二乘三：

{% raw %}<pre class="Agda"><a id="24906" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#24906" class="Function">_</a> <a id="24908" class="Symbol">=</a>
  <a id="24912" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2597" class="Function Operator">begin</a>
    <a id="24922" class="Number">2</a> <a id="24924" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#23683" class="Function Operator">*</a> <a id="24926" class="Number">3</a>
  <a id="24930" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>    <a id="24937" class="Comment">-- 归纳步骤</a>
    <a id="24949" class="Number">3</a> <a id="24951" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#16726" class="Function Operator">+</a> <a id="24953" class="Symbol">(</a><a id="24954" class="Number">1</a> <a id="24956" href="plfa.part1.Naturals.html#23683" class="Function Operator">*</a> <a id="24958" class="Number">3</a><a id="24959" class="Symbol">)</a>
  <a id="24963" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>    <a id="24970" class="Comment">-- 归纳步骤</a>
    <a id="24982" class="Number">3</a> <a id="24984" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#16726" class="Function Operator">+</a> <a id="24986" class="Symbol">(</a><a id="24987" class="Number">3</a> <a id="24989" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="24991" class="Symbol">(</a><a id="24992" class="Number">0</a> <a id="24994" href="plfa.part1.Naturals.html#23683" class="Function Operator">*</a> <a id="24996" class="Number">3</a><a id="24997" class="Symbol">))</a>
  <a id="25002" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>    <a id="25009" class="Comment">-- 起始步骤</a>
    <a id="25021" class="Number">3</a> <a id="25023" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#16726" class="Function Operator">+</a> <a id="25025" class="Symbol">(</a><a id="25026" class="Number">3</a> <a id="25028" href="plfa.part1.Naturals.html#16726" class="Function Operator">+</a> <a id="25030" class="Number">0</a><a id="25031" class="Symbol">)</a>
  <a id="25035" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>    <a id="25042" class="Comment">-- 化简</a>
    <a id="25052" class="Number">6</a>
  <a id="25056" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2892" class="Function Operator">∎</a>
</pre>{% endraw %}
{::comment}
The first line matches the inductive case by taking `m = 1` and `n = 3`,
The second line matches the inductive case by taking `m = 0` and `n = 3`,
and the third line matches the base case by taking `n = 3`.
Here we have omitted the signature declaring `_ : 2 * 3 ≡ 6`, since
it can easily be inferred from the corresponding term.
{:/}

第一行取 `m = 1` 和 `n = 3` 匹配了归纳步骤，第二行取 `m = 0` 和 `n = 3`
匹配了归纳步骤，最后第三行取 `n = 3` 匹配了起始步骤。在这里我们省略了
`_ : 2 * 3 ≡ 6` 的签名，因为它很容易从对应的项推导出来。

{::comment}
#### Exercise `*-example` (practice) {#times-example}
{:/}

#### 练习 `*-example`（实践） {#times-example}

{::comment}
Compute `3 * 4`, writing out your reasoning as a chain of equations.
{:/}

计算 `3 * 4`，将你的推导过程写成等式链。

{::comment}
{% raw %}<pre class="Agda"><a id="25786" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="25823" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}
{::comment}
Exercise `_^_` (recommended)
{:/}

#### 练习 `_^_`（推荐） {#power}

{::comment}
Define exponentiation, which is given by the following equations:
{:/}

根据以下等式写出乘方的定义。

    m ^ 0        =  1
    m ^ (1 + n)  =  m * (m ^ n)

{::comment}
Check that `3 ^ 4` is `81`.
{:/}

检查 `3 ^ 4` 是否等于 `81`。

{::comment}
{% raw %}<pre class="Agda"><a id="26156" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="26193" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}
{::comment}
Monus
{:/}

## 饱和减法

{::comment}
We can also define subtraction.  Since there are no negative
natural numbers, if we subtract a larger number from a smaller
number we will take the result to be zero.  This adaption of
subtraction to naturals is called _monus_ (a twist on _minus_).
{:/}

我们也可以定义减法。由于没有负的自然数，如果被减数比减数小，我们就将结果取零。这种针对自然数的减法变种称作**饱和减法（Monus，由 minus 修改而来）**。

{::comment}
Monus is our first use of a definition that uses pattern
matching against both arguments:
{:/}

饱和减法是我们首次在定义中对两个参数都使用模式匹配：

{% raw %}<pre class="Agda"><a id="_∸_"></a><a id="26736" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#26736" class="Function Operator">_∸_</a> <a id="26740" class="Symbol">:</a> <a id="26742" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a> <a id="26744" class="Symbol">→</a> <a id="26746" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a> <a id="26748" class="Symbol">→</a> <a id="26750" href="plfa.part1.Naturals.html#1621" class="Datatype">ℕ</a>
<a id="26752" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#26752" class="Bound">m</a>     <a id="26758" href="plfa.part1.Naturals.html#26736" class="Function Operator">∸</a> <a id="26760" href="plfa.part1.Naturals.html#1637" class="InductiveConstructor">zero</a>   <a id="26767" class="Symbol">=</a>  <a id="26770" href="plfa.part1.Naturals.html#26752" class="Bound">m</a>
<a id="26772" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1637" class="InductiveConstructor">zero</a>  <a id="26778" href="plfa.part1.Naturals.html#26736" class="Function Operator">∸</a> <a id="26780" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="26784" href="plfa.part1.Naturals.html#26784" class="Bound">n</a>  <a id="26787" class="Symbol">=</a>  <a id="26790" href="plfa.part1.Naturals.html#1637" class="InductiveConstructor">zero</a>
<a id="26795" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#1648" class="InductiveConstructor">suc</a> <a id="26799" href="plfa.part1.Naturals.html#26799" class="Bound">m</a> <a id="26801" href="plfa.part1.Naturals.html#26736" class="Function Operator">∸</a> <a id="26803" href="plfa.part1.Naturals.html#1648" class="InductiveConstructor">suc</a> <a id="26807" href="plfa.part1.Naturals.html#26807" class="Bound">n</a>  <a id="26810" class="Symbol">=</a>  <a id="26813" href="plfa.part1.Naturals.html#26799" class="Bound">m</a> <a id="26815" href="plfa.part1.Naturals.html#26736" class="Function Operator">∸</a> <a id="26817" href="plfa.part1.Naturals.html#26807" class="Bound">n</a>
</pre>{% endraw %}
{::comment}
We can do a simple analysis to show that all the cases are covered.
{:/}

我们可以通过简单的分析来说明所有的情况都被考虑了。

{::comment}
   Consider the second argument.
     If it is `zero`, then the first equation applies.
     If it is `suc n`, then consider the first argument.
       If it is `zero`, then the second equation applies.
       If it is `suc m`, then the third equation applies.
{:/}

  * 考虑第二个参数。
    + 如果它是 `zero`，应用第一个等式。
    + 如果它是 `suc n`，考虑第一个参数。
      - 如果它是 `zero`，应用第二个等式。
      - 如果它是 `suc m`，应用第三个等式。

{::comment}
Again, the recursive definition is well founded because
monus on bigger numbers is defined in terms of monus on
smaller numbers.
{:/}

此也是良基的，因为较大的数的饱和减法是用较小的数的饱和减法定义的。

{::comment}
For example, let's subtract two from three:
{:/}

例如，我们来计算三减二：

{% raw %}<pre class="Agda"><a id="27606" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#27606" class="Function">_</a> <a id="27608" class="Symbol">=</a>
  <a id="27612" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2597" class="Function Operator">begin</a>
    <a id="27622" class="Number">3</a> <a id="27624" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#26736" class="Function Operator">∸</a> <a id="27626" class="Number">2</a>
  <a id="27630" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>
    <a id="27638" class="Number">2</a> <a id="27640" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#26736" class="Function Operator">∸</a> <a id="27642" class="Number">1</a>
  <a id="27646" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>
    <a id="27654" class="Number">1</a> <a id="27656" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#26736" class="Function Operator">∸</a> <a id="27658" class="Number">0</a>
  <a id="27662" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>
    <a id="27670" class="Number">1</a>
  <a id="27674" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2892" class="Function Operator">∎</a>
</pre>{% endraw %}
{::comment}
We did not use the second equation at all, but it will be required
if we try to subtract a larger number from a smaller one:
{:/}

我们没有使用第二个等式，但是如果被减数比减数小，我们还是会用到它。

{% raw %}<pre class="Agda"><a id="27863" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#27863" class="Function">_</a> <a id="27865" class="Symbol">=</a>
  <a id="27869" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2597" class="Function Operator">begin</a>
    <a id="27879" class="Number">2</a> <a id="27881" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#26736" class="Function Operator">∸</a> <a id="27883" class="Number">3</a>
  <a id="27887" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>
    <a id="27895" class="Number">1</a> <a id="27897" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#26736" class="Function Operator">∸</a> <a id="27899" class="Number">2</a>
  <a id="27903" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>
    <a id="27911" class="Number">0</a> <a id="27913" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#26736" class="Function Operator">∸</a> <a id="27915" class="Number">1</a>
  <a id="27919" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2655" class="Function Operator">≡⟨⟩</a>
    <a id="27927" class="Number">0</a>
  <a id="27931" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#2892" class="Function Operator">∎</a>
</pre>{% endraw %}
{::comment}
Exercise `∸-examples` (recommended)
{:/}

练习 `∸-examples`（推荐） {#monus-examples}

{::comment}
Compute `5 ∸ 3` and `3 ∸ 5`, writing out your reasoning as a chain of equations.
{:/}

计算 `5 ∸ 3` 和 `3 ∸ 5`，将你的推导过程写成等式链。

{::comment}
{% raw %}<pre class="Agda"><a id="28182" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="28219" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}
{::comment}
Precedence
{:/}

## 优先级

{::comment}
We often use _precedence_ to avoid writing too many parentheses.
Application _binds more tightly than_ (or _has precedence over_) any
operator, and so we may write `suc m + n` to mean `(suc m) + n`.
As another example, we say that multiplication binds more tightly than
addition, and so write `n + m * n` to mean `n + (m * n)`.
We also sometimes say that addition _associates to the left_, and
so write `m + n + p` to mean `(m + n) + p`.
{:/}

我们经常使用**优先级（Precedence）**来避免书写大量的括号。函数应用比其它任何运算符都**结合得更紧密**（即**有更高的优先级**），所以我们可以用 `suc m + n` 来表示 `(suc m) + n`。另一个例子是，我们说乘法比加法结合得更紧密，所以可以用 `n + m * n` 来表示 `n + (m * n)`。我们有时候也说加法是**左结合的**，所以可以用 `m + n + p` 来表示 `(m + n) + p`。

{::comment}
In Agda the precedence and associativity of infix operators
needs to be declared:
{:/}

在 Agda 中，中缀运算符的优先级和结合性需要被声明：

{% raw %}<pre class="Agda"><a id="29095" class="Keyword">infixl</a> <a id="29102" class="Number">6</a>  <a id="29105" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#16726" class="Primitive Operator">_+_</a>  <a id="29110" href="plfa.part1.Naturals.html#26736" class="Primitive Operator">_∸_</a>
<a id="29114" class="Keyword">infixl</a> <a id="29121" class="Number">7</a>  <a id="29124" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#23683" class="Primitive Operator">_*_</a>
</pre>{% endraw %}
{::comment}
This states operators `_+_` and `_∸_` have precedence level 6,
and operator `_*_` has precedence level 7.
Addition and monus bind less tightly than multiplication
because they have lower precedence.
Writing `infixl` indicates that all three
operators associate to the left.  One can also write `infixr` to
indicate that an operator associates to the right, or just `infix` to
indicate that parentheses are always required to disambiguate.
{:/}

它声明了运算符 `_+_` 和 `_∸_` 的优先级为 6，运算符 `_*_` 的优先级为 7。因为加法和饱和减法的优先级更低，所以它们结合得不如乘法紧密。
`infixl` 意味着三个运算符都是左结合的。编写者也可以用 `infixr` 来表示某个运算符是右结合的，或者用 `infix` 来表示总是需要括号来消除歧义。

{::comment}
Currying
{:/}

## 柯里化

{::comment}
We have chosen to represent a function of two arguments in terms
of a function of the first argument that returns a function of the
second argument.  This trick goes by the name _currying_.
{:/}

我们曾将接受两个参数的函数表示成「接受第一个参数，返回接受第二个参数的函数」的函数。这种技巧叫做**柯里化（Currying）**。

{::comment}
Agda, like other functional languages such as Haskell and ML,
is designed to make currying easy to use.  Function
arrows associate to the right and application associates to the left
{:/}

与 Haskell 和 ML 等函数式语言类似，Agda 在设计时就考虑了让柯里化更加易用。函数箭头是右结合的，而函数应用是左结合的。

比如

{::comment}
`ℕ → ℕ → ℕ` stands for `ℕ → (ℕ → ℕ)`

and

`_+_ 2 3` stands for `(_+_ 2) 3`.
{:/}

`ℕ → ℕ → ℕ` 表示 `ℕ → (ℕ → ℕ)`

而

`_+_ 2 3` 表示 `(_+_ 2) 3`。

{::comment}
The term `_+_ 2` by itself stands for the function that adds two to
its argument, hence applying it to three yields five.
{:/}

`_+_ 2` 这个项表示一个「将参数加二」的函数，因此将它应用到三就得到了五。

{::comment}
Currying is named for Haskell Curry, after whom the programming
language Haskell is also named.  Curry's work dates to the 1930's.
When I first learned about currying, I was told it was misattributed,
since the same idea was previously proposed by Moses Schönfinkel in
the 1920's.  I was told a joke: "It should be called schönfinkeling,
but currying is tastier". Only later did I learn that the explanation
of the misattribution was itself a misattribution.  The idea actually
appears in the _Begriffschrift_ of Gottlob Frege, published in 1879.
{:/}

柯里化是以哈斯凯尔·柯里（Haskell Curry）的名字命名的，编程语言 Haskell 也是。柯里的工作可以追溯到 19 世纪 30 年代。当我第一次了解到柯里化时，有人告诉我柯里化的命名是个归因错误，因为在 20 年代同样的想法就已经被
Moses Schönfinkel 提出了。我也听说过这样一个笑话：「（柯里化）本来该命名成
Schönfinkel 化的，但是咖喱（Curry）更好吃」。直到之后我才了解到，这个归因错误的解释本身也是个归因错误。柯里化的概念早在戈特洛布·弗雷格
（Gottlob Frege）发表于 1879 年的 **"Begriffsschrift"（《概念文字》）**中就出现了。

{::comment}
The story of creation, revisited
{:/}

## 又一个创世故事

{::comment}
Just as our inductive definition defines the naturals in terms of the
naturals, so does our recursive definition define addition in terms
of addition.
{:/}

和归纳定义中用自然数定义了自然数一样，递归定义也用加法定义了加法。

{::comment}
Again, it is possible to assign our definition a meaning without
resorting to unpermitted circularities.  We do so by reducing our
definition to equivalent inference rules for judgments about equality:
{:/}

同理，无需利用循环性，我们的加法定义也是可以被赋予意义的。为此，我们需要将加法的定义规约到用于判断相等性的等价的推导规则上来。

    n : ℕ
    --------------
    zero + n  =  n

    m + n  =  p
    ---------------------
    (suc m) + n  =  suc p

{::comment}
Here we assume we have already defined the infinite set of natural
numbers, specifying the meaning of the judgment `n : ℕ`.  The first
inference rule is the base case.  It asserts that if `n` is a natural number
then adding zero to it gives `n`.  The second inference rule is the inductive
case. It asserts that if adding `m` and `n` gives `p`, then adding `suc m` and
`n` gives `suc p`.
{:/}

假设我们已经定义了自然数的无限集合，指定了判断 `n : ℕ` 的意义。第一条推导规则是起始步骤。它断言如果 `n` 是一个自然数，那么零加上它得 `n`。第二条推导规则是归纳步骤。它断言如果 `m` 加上 `n` 得 `p`，那么 `suc m` 加上 `n` 得 `suc p`。

{::comment}
Again we resort to a creation story, where this time we are
concerned with judgments about addition:
{:/}

我们同样借创世故事来帮助理解，不过这次关注的是关于加法的判断。

{::comment}
    -- In the beginning, we know nothing about addition.
{:/}

    -- 起初，我们对加法一无所知。

{::comment}
Now, we apply the rules to all the judgment we know about.
The base case tells us that `zero + n = n` for every natural `n`,
so we add all those equations.  The inductive case tells us that if
`m + n = p` (on the day before today) then `suc m + n = suc p`
(today).  We didn't know any equations about addition before today,
so that rule doesn't give us any new equations:
{:/}

现在对所有已知的判断应用之前的规则。起始步骤告诉我们，对于每个自然数 `n` 都有 `zero + n = n`，因此我们添加所有的这类等式。归纳步骤告诉我们，如果「昨天」有 `m + n = p`，那么「今天」
就有 `suc m + n = suc p`。在今天之前，我们不知道任何关于加法的等式，因此这条规则不会给我们任何新的等式。

{::comment}
    -- On the first day, we know about addition of 0.
    0 + 0 = 0     0 + 1 = 1    0 + 2 = 2     ...
{:/}

    -- 第一天，我们知道了 0 为被加数的加法。
    0 + 0 = 0     0 + 1 = 1    0 + 2 = 2     ...

{::comment}
Then we repeat the process, so on the next day we know about all the
equations from the day before, plus any equations added by the rules.
The base case tells us nothing new, but now the inductive case adds
more equations:
{:/}

然后我们重复这个过程。今天我们知道来自昨天的所有等式，以及任何通过规则添加的等式。起始步骤没有告诉我们任何新东西，但是归纳步骤添加了更多的等式。

{::comment}
    -- On the second day, we know about addition of 0 and 1.
    0 + 0 = 0     0 + 1 = 1     0 + 2 = 2     0 + 3 = 3     ...
    1 + 0 = 1     1 + 1 = 2     1 + 2 = 3     1 + 3 = 4     ...
{:/}

    -- 第二天，我们知道了 0，1 为被加数的加法。
    0 + 0 = 0     0 + 1 = 1     0 + 2 = 2     0 + 3 = 3     ...
    1 + 0 = 1     1 + 1 = 2     1 + 2 = 3     1 + 3 = 4     ...

{::comment}
And we repeat the process again:
{:/}

我们再次重复这个过程：

{::comment}
    -- On the third day, we know about addition of 0, 1, and 2.
    0 + 0 = 0     0 + 1 = 1     0 + 2 = 2     0 + 3 = 3     ...
    1 + 0 = 1     1 + 1 = 2     1 + 2 = 3     1 + 3 = 4     ...
    2 + 0 = 2     2 + 1 = 3     2 + 2 = 4     2 + 3 = 5     ...
{:/}

    -- 第三天，我们知道了 0，1，2 为被加数的加法。
    0 + 0 = 0     0 + 1 = 1     0 + 2 = 2     0 + 3 = 3     ...
    1 + 0 = 1     1 + 1 = 2     1 + 2 = 3     1 + 3 = 4     ...
    2 + 0 = 2     2 + 1 = 3     2 + 2 = 4     2 + 3 = 5     ...

{::comment}
You've got the hang of it by now:
{:/}

此时规律已经很明显了：

{::comment}
    -- On the fourth day, we know about addition of 0, 1, 2, and 3.
    0 + 0 = 0     0 + 1 = 1     0 + 2 = 2     0 + 3 = 3     ...
    1 + 0 = 1     1 + 1 = 2     1 + 2 = 3     1 + 3 = 4     ...
    2 + 0 = 2     2 + 1 = 3     2 + 2 = 4     2 + 3 = 5     ...
    3 + 0 = 3     3 + 1 = 4     3 + 2 = 5     3 + 3 = 6     ...
{:/}

    -- 第四天，我们知道了 0，1，2，3 为被加数的加法。
    0 + 0 = 0     0 + 1 = 1     0 + 2 = 2     0 + 3 = 3     ...
    1 + 0 = 1     1 + 1 = 2     1 + 2 = 3     1 + 3 = 4     ...
    2 + 0 = 2     2 + 1 = 3     2 + 2 = 4     2 + 3 = 5     ...
    3 + 0 = 3     3 + 1 = 4     3 + 2 = 5     3 + 3 = 6     ...

{::comment}
The process continues.  On the _m_'th day we will know all the
equations where the first number is less than _m_.
{:/}

此过程可以继续下去。在第 *m* 天我们将知道所有被加数小于 *m* 的等式。

{::comment}
As we can see, the reasoning that justifies inductive and recursive
definitions is quite similar.  They might be considered two sides of
the same coin.
{:/}

如上所示，归纳定义和递归定义的的推导过程十分相似。它们就像一枚硬币的两面。

{::comment}
## The story of creation, finitely {#finite-creation}
{:/}

## 有限的创世故事 {#finite-creation}

{::comment}
The above story was told in a stratified way.  First, we create
the infinite set of naturals.  We take that set as given when
creating instances of addition, so even on day one we have an
infinite set of instances.
{:/}

前面的创世故事是用分层的方式讲述的。首先，我们创造了自然数的无限集合。然后，我们构造加法的实例时把自然数集视为现成的，所以即使在第一天我们也有一个无限的实例集合。

{::comment}
Instead, we could choose to create both the naturals and the instances
of addition at the same time. Then on any day there would be only
a finite set of instances:
{:/}

然而，我们也可以选择同时构造自然数集和加法的实例。这样在任何一天都只会有一个有限的实例集合。

{::comment}
    -- In the beginning, we know nothing.
{:/}

    -- 起初，我们一无所知。

{::comment}
Now, we apply the rules to all the judgment we know about.  Only the
base case for naturals applies:
{:/}

现在，对我们已知的所有判断应用之前的规则。只有自然数的起始步骤适用：

{::comment}
    -- On the first day, we know zero.
    0 : ℕ
{:/}

    -- 第一天，我们知道了零。
    0 : ℕ

{::comment}
Again, we apply all the rules we know.  This gives us a new natural,
and our first equation about addition.
{:/}

我们再次应用所有的规则。这次我们有了一个新自然数，和加法的第一个等式。

{::comment}
    -- On the second day, we know one and all sums that yield zero.
    0 : ℕ
    1 : ℕ    0 + 0 = 0
{:/}

    -- 第二天，我们知道了一和所有和为零的加法算式。
    0 : ℕ
    1 : ℕ    0 + 0 = 0

{::comment}
Then we repeat the process.  We get one more equation about addition
from the base case, and also get an equation from the inductive case,
applied to equation of the previous day:
{:/}

然后我们重复这个过程。我们通过加法的起始步骤得到了一个等式，也通过在前一天的等式上应用加法的归纳步骤得到了一个等式：

{::comment}
    -- On the third day, we know two and all sums that yield one.
    0 : ℕ
    1 : ℕ    0 + 0 = 0
    2 : ℕ    0 + 1 = 1   1 + 0 = 1
{:/}

    -- 第三天，我们知道了二和所有和为一的加法算式。
    0 : ℕ
    1 : ℕ    0 + 0 = 0
    2 : ℕ    0 + 1 = 1   1 + 0 = 1

{::comment}
You've got the hang of it by now:
{:/}

此时规律已经很明显了：

{::comment}
    -- On the fourth day, we know three and all sums that yield two.
    0 : ℕ
    1 : ℕ    0 + 0 = 0
    2 : ℕ    0 + 1 = 1   1 + 0 = 1
    3 : ℕ    0 + 2 = 2   1 + 1 = 2    2 + 0 = 2
{:/}

    -- 第四天，我们知道了三和所有和为二的加法算式。
    0 : ℕ
    1 : ℕ    0 + 0 = 0
    2 : ℕ    0 + 1 = 1   1 + 0 = 1
    3 : ℕ    0 + 2 = 2   1 + 1 = 2    2 + 0 = 2

{::comment}
On the _n_'th day there will be _n_ distinct natural numbers, and
_n × (n-1) / 2_ equations about addition.  The number _n_ and all equations
for addition of numbers less than _n_ first appear by day _n+1_.
This gives an entirely finitist view of infinite sets of data and
equations relating the data.
{:/}

在第 _n_ 天会有 _n_ 个不同的自然数和 _n × (n-1) / 2_ 个加法等式。数字 _n_ 和所有和小于 _n_ 的加法等式在第 _n+1_ 天首次出现。这提供了一种无限的数据集合及与之相关的等式的有限主义视角。

{::comment}
Writing definitions interactively
{:/}

## 交互式地编写定义

{::comment}
Agda is designed to be used with the Emacs text editor, and the two
in combination provide features that help to create definitions
and proofs interactively.
{:/}

Agda 被设计为使用 Emacs 作为文本编辑器，二者一同提供了很多能帮助用户交互式地创建定义和证明的功能。

{::comment}
Begin by typing:
{:/}

我们从输入以下代码开始：

    _+_ : ℕ → ℕ → ℕ
    m + n = ?

{::comment}
The question mark indicates that you would like Agda to help with
filling in that part of the code. If you type `C-c C-l` (pressing
the control key while hitting the `c` key followed by the `l` key)
the question mark will be replaced:
{:/}

问号表示你希望 Agda 帮助你填入这部分代码。如果按下组合键 `C-c C-l`
（按住 Control 键的同时先按 `c` 键再按 `l` 键），这个问号会被替换：

    _+_ : ℕ → ℕ → ℕ
    m + n = { }0

{::comment}
The empty braces are called a *hole*, and 0 is a number used for
referring to the hole.  The hole will display highlighted in green.
Emacs will also create a window displaying the text
{:/}

这对花括号被称作一个**洞（Hole）**，0 是这个洞的编号。洞将会被高亮显示为绿色（或蓝色）。同时，Emacs 会创建一个窗口显示如下文字：

    ?0 : ℕ

{::comment}
to indicate that hole 0 is to be filled in with a term of type `ℕ`.
Typing `C-c C-f` will move you into the next hole.
{:/}

这表示 0 号洞需要填入一个类型为 `ℕ` 的项。按组合键 `C-c C-f` 会移动到下一个洞。

{::comment}
We wish to define addition by recursion on the first argument.
Move the cursor into the hole and type `C-c C-c`.   You will be given
the prompt:
{:/}

我们希望在第一个参数上递归来定义加法。将光标移至 0 号洞并按 `C-c C-c`，你将看见如下提示：

    pattern variables to case (empty for split on result):

即「用于分项的模式变量（留空以对结果分项）：」。

{::comment}
Typing `m` will cause a split on that variable, resulting
in an update to the code:
{:/}

键入 `m` 会对名为 `m` 的变量分项（即自动模式匹配），并将代码更新为：

    _+_ : ℕ → ℕ → ℕ
    zero + n = { }0
    suc m + n = { }1

{::comment}
There are now two holes, and the window at the bottom tells you the
required type of each:
{:/}

现在有两个洞了。底部的窗口会告诉你每个洞所需的类型：

    ?0 : ℕ
    ?1 : ℕ

{::comment}
Going into hole 0 and type `C-c C-,` will display information on the
required type of the hole, and what free variables are available:
{:/}

移动至 0 号洞，按下 `C-c C-,` 会显示当前洞所需类型的具体信息，以及可用的自由变量：

    Goal: ℕ
    ————————————————————————————————————————————————————————————
    n : ℕ

{::comment}
This strongly suggests filling the hole with `n`.  After the hole is
filled, you can type `C-c C-space`, which will remove the hole:
{:/}

这些信息强烈建议了用 `n` 填入该洞。填入内容后，你可以按下 `C-c C-空格`
来移除这个洞。

    _+_ : ℕ → ℕ → ℕ
    zero + n = n
    suc m + n = { }1

{::comment}
Again, going into hole 1 and type `C-c C-,` will display information on the
required type of the hole, and what free variables are available:
{:/}

同理，移动到 1 号洞并按下 `C-c C-,` 会显示当前洞所需类型的具体信息，以及可用的自由变量：

    Goal: ℕ
    ————————————————————————————————————————————————————————————
    n : ℕ
    m : ℕ

{::comment}
Going into the hole and type `C-c C-r` will fill it in with a constructor
(if there is a unique choice) or tell you what constructors you might use,
if there is a choice.  In this case, it displays the following:
{:/}

移动到一个洞并按下 `C-c C-r` 会将一个构造子填入这个洞（如果有唯一的选择的话），或者告诉你有哪些可用的构造子以供选择。在当前情况下，编辑器会显示如下内容：

    Don't know which constructor to introduce of zero or suc

即“不知道在 `zero` 和 `suc` 中该引入哪一个构造子”。

{::comment}
Filling the hole with `suc ?` and typing `C-c C-space` results in the following:
{:/}

我们将 `suc ?` 填入并按下 `C-c C-空格`，它会将代码更新为：

    _+_ : ℕ → ℕ → ℕ
    zero + n = n
    suc m + n = suc { }1

{::comment}
Going into the new hole and typing `C-c C-,` gives similar information to before:
{:/}

移动到新的洞并按下 `C-c C-,` 给出了和之前类似的信息：

    Goal: ℕ
    ————————————————————————————————————————————————————————————
    n : ℕ
    m : ℕ

{::comment}
We can fill the hole with `m + n` and type `C-c C-space` to complete the program:
{:/}

我们可以用 `m + n` 填入该洞并按 `C-c C-空格` 来完成程序：

    _+_ : ℕ → ℕ → ℕ
    zero + n = n
    suc m + n = suc (m + n)

{::comment}
Exploiting interaction to this degree is probably not helpful for a program this
simple, but the same techniques can help with more complex programs.  Even for
a program this simple, using `C-c C-c` to split cases can be helpful.
{:/}

在如此简单的程序上频繁使用交互操作可能帮助不大，但是同样的技巧能够帮助你构建更复杂的程序。甚至对于加法定义这么简单的程序，使用
`C-c C-c` 来分项仍然是有用的。

{::comment}
More pragmas
{:/}

## 更多编译指令

{::comment}
Including the lines
{:/}

{% raw %}<pre class="Agda"><a id="43057" class="Symbol">{-#</a> <a id="43061" class="Keyword">BUILTIN</a> <a id="43069" class="Pragma">NATPLUS</a> <a id="43077" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#16726" class="Primitive Operator">_+_</a> <a id="43081" class="Symbol">#-}</a>
<a id="43085" class="Symbol">{-#</a> <a id="43089" class="Keyword">BUILTIN</a> <a id="43097" class="Pragma">NATTIMES</a> <a id="43106" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#23683" class="Primitive Operator">_*_</a> <a id="43110" class="Symbol">#-}</a>
<a id="43114" class="Symbol">{-#</a> <a id="43118" class="Keyword">BUILTIN</a> <a id="43126" class="Pragma">NATMINUS</a> <a id="43135" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#26736" class="Primitive Operator">_∸_</a> <a id="43139" class="Symbol">#-}</a>
</pre>{% endraw %}
{::comment}
tells Agda that these three operators correspond to the usual ones,
and enables it to perform these computations using the corresponding
Haskell operators on the arbitrary-precision integer type.
Representing naturals with `zero` and `suc` requires time proportional
to _m_ to add _m_ and _n_, whereas representing naturals as integers
in Haskell requires time proportional to the larger of the logarithms
of _m_ and _n_.  Similarly, representing naturals with `zero`
and `suc` requires time proportional to the product of _m_ and _n_ to
multiply _m_ and _n_, whereas representing naturals as integers in
Haskell requires time proportional to the sum of the logarithms of
_m_ and _n_.
{:/}

以上几行告诉 Agda 这几个运算符和数学中常用的运算符相对应，以便让它在计算时使用相应的，可处理任意精度整数类型的 Haskell 运算符。计算 `m` 加 `n` 时，用 `zero` 和 `suc` 表示的自然数需要正比于 `m` 的时间，而用 Haskell 整数表示的情况下只需要正比于 `m` 和 `n` 中较大者的对数的时间。类似地，计算 `m` 乘 `n` 时，用 `zero` 和 `suc` 表示的自然数需要正比于 `m` 乘 `n` 的时间，而用 Haskell 整数表示的情况下只需要正比于 `m` 和 `n` 的对数之和的时间。

{::comment}
Exercise `Bin` (stretch)
{:/}

#### 练习 `Bin`（拓展） {#Bin}

{::comment}
A more efficient representation of natural numbers uses a binary
rather than a unary system.  We represent a number as a bitstring:
{:/}

使用二进制系统能提供比一进制系统更高效的自然数表示。我们可以用一个比特串来表示一个数：

{% raw %}<pre class="Agda"><a id="44403" class="Keyword">data</a> <a id="Bin"></a><a id="44408" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#44408" class="Datatype">Bin</a> <a id="44412" class="Symbol">:</a> <a id="44414" class="PrimitiveType">Set</a> <a id="44418" class="Keyword">where</a>
  <a id="Bin.⟨⟩"></a><a id="44426" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#44426" class="InductiveConstructor">⟨⟩</a> <a id="44429" class="Symbol">:</a> <a id="44431" href="plfa.part1.Naturals.html#44408" class="Datatype">Bin</a>
  <a id="Bin._O"></a><a id="44437" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#44437" class="InductiveConstructor Operator">_O</a> <a id="44440" class="Symbol">:</a> <a id="44442" href="plfa.part1.Naturals.html#44408" class="Datatype">Bin</a> <a id="44446" class="Symbol">→</a> <a id="44448" href="plfa.part1.Naturals.html#44408" class="Datatype">Bin</a>
  <a id="Bin._I"></a><a id="44454" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Naturals.md %}{% raw %}#44454" class="InductiveConstructor Operator">_I</a> <a id="44457" class="Symbol">:</a> <a id="44459" href="plfa.part1.Naturals.html#44408" class="Datatype">Bin</a> <a id="44463" class="Symbol">→</a> <a id="44465" href="plfa.part1.Naturals.html#44408" class="Datatype">Bin</a>
</pre>{% endraw %}
{::comment}
For instance, the bitstring
{:/}

例如，以下比特串

    1011

{::comment}
standing for the number eleven is encoded as
{:/}

代表数字十一被编码为了

    ⟨⟩ I O I I

{::comment}
Representations are not unique due to leading zeros.
Hence, eleven is also represented by `001011`, encoded as:
{:/}

由于前导零的存在，表示并不是唯一的。因此，十一同样可以表示成 `001011`，编码为：

    ⟨⟩ O I O I I

{::comment}
Define a function
{:/}

定义这样一个函数

    inc : Bin → Bin

{::comment}
that converts a bitstring to the bitstring for the next higher
number.  For example, since `1100` encodes twelve, we should have:
{:/}

将一个比特串转换成下一个数的比特串。比如，`1100` 编码了十二，我们就应该有：

    inc (⟨⟩ I O I I) ≡ ⟨⟩ I I O O

{::comment}
Confirm that this gives the correct answer for the bitstrings
encoding zero through four.
{:/}

实现这个函数，并验证它对于表示零到四的比特串都能给出正确结果。

{::comment}
Using the above, define a pair of functions to convert
between the two representations.
{:/}

使用以上的定义，再定义一对函数用于在两种表示间转换。

    to   : ℕ → Bin
    from : Bin → ℕ

{::comment}
For the former, choose the bitstring to have no leading zeros if it
represents a positive natural, and represent zero by `⟨⟩ O`.
Confirm that these both give the correct answer for zero through four.
{:/}

对于前者，用没有前导零的比特串来表示正数，并用 `x0 nil` 表示零。验证这两个函数都能对零到四给出正确结果。

{::comment}
{% raw %}<pre class="Agda"><a id="45728" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="45765" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}
{::comment}
Standard library
{:/}

## 标准库

{::comment}
At the end of each chapter, we will show where to find relevant
definitions in the standard library.  The naturals, constructors for
them, and basic operators upon them, are defined in the standard
library module `Data.Nat`:
{:/}

在每一章的结尾，我们将展示如何在标准库中找到相关的定义。自然数，它们的构造子，以及用于自然数的基本运算符，都在标准库模块 `Data.Nat` 中定义：

{% raw %}<pre class="Agda"><a id="46152" class="Comment">-- import Data.Nat using (ℕ; zero; suc; _+_; _*_; _^_; _∸_)</a>
</pre>{% endraw %}
{::comment}
Normally, we will show an import as running code, so Agda will
complain if we attempt to import a definition that is not available.
This time, however, we have only shown the import as a comment.  Both
this chapter and the standard library invoke the `NATURAL` pragma, the
former on `ℕ`, and the latter on the equivalent type `Data.Nat.ℕ`.
Such a pragma can only be invoked once, as invoking it twice would
raise confusion as to whether `2` is a value of type `ℕ` or type
`Data.Nat.ℕ`.  Similar confusions arise if other pragmas are invoked
twice. For this reason, we will usually avoid pragmas in future chapters.
Information on pragmas can be found in the Agda documentation.
{:/}

正常情况下，我们会以运行代码的形式展示一个导入语句，这样如果我们尝试导入一个不可用的定义，Agda 就会报错。不过现在，我们只在注释里展示了这个导入语句。这一章和标准库都调用了 `NATURAL` 编译指令。我们是在 `ℕ` 上使用，而标准库是在等价的类型 `Data.Nat.ℕ` 上使用。这样的编译指令只能被调用一次，因为重复调用会导致 `2` 到底是类型 `ℕ` 的值还是类型 `Data.Nat.ℕ` 的值这样的困惑。重复调用其它的编译指令也会导致同样的问题。基于这个原因，我们在后续章节中通常会避免使用编译指令。更多关于编译指令的信息可在
Agda 文档中找到。

{::comment}
Unicode
{:/}

## Unicode

{::comment}
This chapter uses the following unicode:

    ℕ  U+2115  DOUBLE-STRUCK CAPITAL N (\bN)
    →  U+2192  RIGHTWARDS ARROW (\to, \r, \->)
    ∸  U+2238  DOT MINUS (\.-)
    ≡  U+2261  IDENTICAL TO (\==)
    ⟨  U+27E8  MATHEMATICAL LEFT ANGLE BRACKET (\<)
    ⟩  U+27E9  MATHEMATICAL RIGHT ANGLE BRACKET (\>)
    ∎  U+220E  END OF PROOF (\qed)
{:/}

这一章使用了如下的 Unicode 符号：

    ℕ  U+2115  双线体大写 N (\bN)
    →  U+2192  右箭头 (\to, \r, \->)
    ∸  U+2238  点减 (\.-)
    ≡  U+2261  等价于 (\==)
    ⟨  U+27E8  数学左尖括号 (\<)
    ⟩  U+27E9  数学右尖括号 (\>)
    ∎  U+220E  证毕 (\qed)

{::comment}
Each line consists of the Unicode character (`ℕ`), the corresponding
code point (`U+2115`), the name of the character (`DOUBLE-STRUCK CAPITAL N`),
and the sequence to type into Emacs to generate the character (`\bN`).
{:/}

以上的每一行均包含 Unicode 符号（如 `ℕ`），对应的 Unicode 码点（如 `U+2115`），符号的名称（如 `双线体大写 N`），以及用于在 Emacs 中键入该符号的按键序列（如 `\bN`）。

{::comment}
The command `\r` gives access to a wide variety of rightward arrows.
After typing `\r`, one can access the many available arrows by using
the left, right, up, and down keys to navigate.  The command remembers
where you navigated to the last time, and starts with the same
character next time.  The command `\l` works similarly for left arrows.
{:/}

通过 `\r` 命令可以查看多种右箭头符号。在输入 `\r` 后，你可以按左、右、上、下键来查看或选择可用的箭头符号。这个命令会记住你上一次选择的位置，并在下一次使用时从该字符开始。用于输入左箭头的 `\l` 命令的用法与此类似。

{::comment}
In place of left, right, up, and down keys, one may also use control
characters:

    C-b  left (backward one character)
    C-f  right (forward one character)
    C-p  up (to the previous line)
    C-n  down (to the next line)
{:/}

除了在输入箭头的命令中使用左、右、上、下键以外，以下按键也可以起到相同的作用：

    C-b  左（后退一个字符）
    C-f  右（前进一个字符）
    C-p  上（到上一行）
    C-n  下（到下一行）

{::comment}
We write `C-b` to stand for control-b, and similarly.  One can also navigate
left and right by typing the digits that appear in the displayed list.
{:/}

`C-b` 表示按 Control + b，其余同理。你也可以直接输入显示的列表中的数字编号来选择。

{::comment}
For a full list of supported characters, use `agda-input-show-translations` with:
{:/}

要查看所支持字符的完整列表，请执行 `agda-input-show-translations` 命令：

    M-x agda-input-show-translations

{::comment}
All the characters supported by `agda-mode` are shown. We write M-x to stand for
typing `ESC` followed by `x`.
{:/}

这样会显示出 `agda-mode` 中所有支持的字符。我们用 M-x 表示按下 `ESC` 后再按下 `x`。

{::comment}
If you want to know how you input a specific Unicode character in an agda file,
move the cursor onto the character and use `quail-show-key` with:
{:/}

如果你想知道如何在 agda 文件中输入一个特定的 Unicode 字符，请将光标移至该字符上，然后执行 `quail-show-key` 命令：

    M-x quail-show-key

{::comment}
You'll see a key sequence of the character in mini buffer.
If you run `M-x qualy-show-key` on say `∸`, you will see `\.-` for the character.
{:/}

你会在迷你缓冲区中看到输入该字符所需的按键序列。例如，如果你在 `∸` 上执行 `M-x qualy-show-key`，就会看到该字符的按键序列为 `\.-`。
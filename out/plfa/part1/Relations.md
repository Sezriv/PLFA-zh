---
src       : "src/plfa/part1/Relations.lagda.md"
title     : "Relations: 关系的归纳定义"
layout    : page
prev      : /Induction/
permalink : /Relations/
next      : /Equality/
translators : ["Fangyi Zhou"]
progress  : 100
---

{% raw %}<pre class="Agda"><a id="181" class="Keyword">module</a> <a id="188" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}" class="Module">plfa.part1.Relations</a> <a id="209" class="Keyword">where</a>
</pre>{% endraw %}
{::comment}
After having defined operations such as addition and multiplication,
the next step is to define relations, such as _less than or equal_.
{:/}

在定义了加法和乘法等运算以后，下一步我们来定义**关系（Relation）**，比如说**小于等于**。


{::comment}
## Imports
{:/}

## 导入

{% raw %}<pre class="Agda"><a id="470" class="Keyword">import</a> <a id="477" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.html" class="Module">Relation.Binary.PropositionalEquality</a> <a id="515" class="Symbol">as</a> <a id="518" class="Module">Eq</a>
<a id="521" class="Keyword">open</a> <a id="526" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.html" class="Module">Eq</a> <a id="529" class="Keyword">using</a> <a id="535" class="Symbol">(</a><a id="536" href="Agda.Builtin.Equality.html#125" class="Datatype Operator">_≡_</a><a id="539" class="Symbol">;</a> <a id="541" href="Agda.Builtin.Equality.html#182" class="InductiveConstructor">refl</a><a id="545" class="Symbol">;</a> <a id="547" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#1090" class="Function">cong</a><a id="551" class="Symbol">)</a>
<a id="553" class="Keyword">open</a> <a id="558" class="Keyword">import</a> <a id="565" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.html" class="Module">Data.Nat</a> <a id="574" class="Keyword">using</a> <a id="580" class="Symbol">(</a><a id="581" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="582" class="Symbol">;</a> <a id="584" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a><a id="588" class="Symbol">;</a> <a id="590" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a><a id="593" class="Symbol">;</a> <a id="595" href="Agda.Builtin.Nat.html#298" class="Primitive Operator">_+_</a><a id="598" class="Symbol">)</a>
<a id="600" class="Keyword">open</a> <a id="605" class="Keyword">import</a> <a id="612" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html" class="Module">Data.Nat.Properties</a> <a id="632" class="Keyword">using</a> <a id="638" class="Symbol">(</a><a id="639" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html#11911" class="Function">+-comm</a><a id="645" class="Symbol">)</a>
</pre>{% endraw %}

{::comment}
## Defining relations
{:/}

## 定义关系

{::comment}
The relation _less than or equal_ has an infinite number of
instances.  Here are a few of them:
{:/}

小于等于这个关系有无穷个实例，如下所示：


    0 ≤ 0     0 ≤ 1     0 ≤ 2     0 ≤ 3     ...
              1 ≤ 1     1 ≤ 2     1 ≤ 3     ...
                        2 ≤ 2     2 ≤ 3     ...
                                  3 ≤ 3     ...
                                            ...

{::comment}
And yet, we can write a finite definition that encompasses
all of these instances in just a few lines.  Here is the
definition as a pair of inference rules:
{:/}

但是，我们仍然可以用几行有限的定义来表示所有的实例，如下文所示的一对推理规则：

    z≤n --------
        zero ≤ n

        m ≤ n
    s≤s -------------
        suc m ≤ suc n

{::comment}
And here is the definition in Agda:
{:/}

以及其 Agda 定义：

{% raw %}<pre class="Agda"><a id="1462" class="Keyword">data</a> <a id="_≤_"></a><a id="1467" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1467" class="Datatype Operator">_≤_</a> <a id="1471" class="Symbol">:</a> <a id="1473" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a> <a id="1475" class="Symbol">→</a> <a id="1477" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a> <a id="1479" class="Symbol">→</a> <a id="1481" class="PrimitiveType">Set</a> <a id="1485" class="Keyword">where</a>

  <a id="_≤_.z≤n"></a><a id="1494" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1494" class="InductiveConstructor">z≤n</a> <a id="1498" class="Symbol">:</a> <a id="1500" class="Symbol">∀</a> <a id="1502" class="Symbol">{</a><a id="1503" href="plfa.part1.Relations.html#1503" class="Bound">n</a> <a id="1505" class="Symbol">:</a> <a id="1507" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="1508" class="Symbol">}</a>
      <a id="1516" class="Comment">--------</a>
    <a id="1529" class="Symbol">→</a> <a id="1531" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a> <a id="1536" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1467" class="Datatype Operator">≤</a> <a id="1538" href="plfa.part1.Relations.html#1503" class="Bound">n</a>

  <a id="_≤_.s≤s"></a><a id="1543" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1543" class="InductiveConstructor">s≤s</a> <a id="1547" class="Symbol">:</a> <a id="1549" class="Symbol">∀</a> <a id="1551" class="Symbol">{</a><a id="1552" href="plfa.part1.Relations.html#1552" class="Bound">m</a> <a id="1554" href="plfa.part1.Relations.html#1554" class="Bound">n</a> <a id="1556" class="Symbol">:</a> <a id="1558" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="1559" class="Symbol">}</a>
    <a id="1565" class="Symbol">→</a> <a id="1567" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1552" class="Bound">m</a> <a id="1569" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="1571" href="plfa.part1.Relations.html#1554" class="Bound">n</a>
      <a id="1579" class="Comment">-------------</a>
    <a id="1597" class="Symbol">→</a> <a id="1599" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="1603" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1552" class="Bound">m</a> <a id="1605" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="1607" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="1611" href="plfa.part1.Relations.html#1554" class="Bound">n</a>
</pre>{% endraw %}
{::comment}
Here `z≤n` and `s≤s` (with no spaces) are constructor names, while
`zero ≤ n`, and `m ≤ n` and `suc m ≤ suc n` (with spaces) are types.
This is our first use of an _indexed_ datatype, where the type `m ≤ n`
is indexed by two naturals, `m` and `n`.  In Agda any line beginning
with two or more dashes is a comment, and here we have exploited that
convention to write our Agda code in a form that resembles the
corresponding inference rules, a trick we will use often from now on.
{:/}

在这里，`z≤n` 和 `s≤s`（无空格）是构造子的名称，`zero ≤ n`、`m ≤ n` 和
`suc m ≤ suc n` （带空格）是类型。在这里我们第一次用到了
**索引数据类型（Indexed datatype）**。我们使用 `m` 和 `n` 这两个自然数来索引
`m ≤ n` 这个类型。在 Agda 里，由两个及以上短横线开始的行是注释行，我们巧妙利用这一语法特性，用上述形式来表示相应的推理规则。在后文中，我们还会继续使用这一形式。

{::comment}
Both definitions above tell us the same two things:

* _Base case_: for all naturals `n`, the proposition `zero ≤ n` holds.
* _Inductive case_: for all naturals `m` and `n`, if the proposition
  `m ≤ n` holds, then the proposition `suc m ≤ suc n` holds.
{:/}

这两条定义告诉我们相同的两件事：

* **起始步骤**: 对于所有的自然数 `n`，命题 `zero ≤ n` 成立。
* **归纳步骤**：对于所有的自然数 `m` 和 `n`，如果命题 `m ≤ n` 成立，
  那么命题 `suc m ≤ suc n` 成立。

{::comment}
In fact, they each give us a bit more detail:

* _Base case_: for all naturals `n`, the constructor `z≤n`
  produces evidence that `zero ≤ n` holds.
* _Inductive case_: for all naturals `m` and `n`, the constructor
  `s≤s` takes evidence that `m ≤ n` holds into evidence that
  `suc m ≤ suc n` holds.
{:/}

实际上，他们分别给我们更多的信息：

* **起始步骤**: 对于所有的自然数 `n`，构造子 `z≤n` 提供了 `zero ≤ n` 成立的证明。
* **归纳步骤**：对于所有的自然数 `m` 和 `n`，构造子 `s≤s` 将 `m ≤ n` 成立的证明
  转化为 `suc m ≤ suc n` 成立的证明。

{::comment}
For example, here in inference rule notation is the proof that
`2 ≤ 4`:
{:/}

例如，我们在这里以推理规则的形式写出 `2 ≤ 4` 的证明：

      z≤n -----
          0 ≤ 2
     s≤s -------
          1 ≤ 3
    s≤s ---------
          2 ≤ 4

{::comment}
And here is the corresponding Agda proof:
{:/}

下面是对应的 Agda 证明：

{% raw %}<pre class="Agda"><a id="3541" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#3541" class="Function">_</a> <a id="3543" class="Symbol">:</a> <a id="3545" class="Number">2</a> <a id="3547" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="3549" class="Number">4</a>
<a id="3551" class="Symbol">_</a> <a id="3553" class="Symbol">=</a> <a id="3555" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1543" class="InductiveConstructor">s≤s</a> <a id="3559" class="Symbol">(</a><a id="3560" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="3564" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a><a id="3567" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
## Implicit arguments
{:/}

## 隐式参数

{::comment}
This is our first use of implicit arguments.  In the definition of
inequality, the two lines defining the constructors use `∀`, very
similar to our use of `∀` in propositions such as:
{:/}

这是我们第一次使用隐式参数。定义不等式时，构造子的定义中使用了 `∀`，就像我们在下面的命题中使用 `∀` 一样：

    +-comm : ∀ (m n : ℕ) → m + n ≡ n + m

{::comment}
However, here the declarations are surrounded by curly braces `{ }`
rather than parentheses `( )`.  This means that the arguments are
_implicit_ and need not be written explicitly; instead, they are
_inferred_ by Agda's typechecker. Thus, we write `+-comm m n` for the
proof that `m + n ≡ n + m`, but `z≤n` for the proof that `zero ≤ n`,
leaving `n` implicit.  Similarly, if `m≤n` is evidence that `m ≤ n`,
we write `s≤s m≤n` for evidence that `suc m ≤ suc n`, leaving both `m`
and `n` implicit.
{:/}

但是我们这里的定义使用了花括号 `{ }`，而不是小括号 `( )`。这意味着参数是**隐式的（Implicit）**，不需要额外声明。实际上，Agda 的类型检查器会**推导（Infer）**出它们。因此，我们在 `m + n ≡ n + m` 的证明中需要写出 `+-comm m n`，在 `zero ≤ n` 的证明中可以省略 `n`。同理，如果 `m≤n` 是 `m ≤ n`的证明，那么我们写出 `s≤s m≤n` 作为 `suc m ≤ suc n` 的证明，无需声明 `m` 和 `n`。

{::comment}
If we wish, it is possible to provide implicit arguments explicitly by
writing the arguments inside curly braces.  For instance, here is the
Agda proof that `2 ≤ 4` repeated, with the implicit arguments made
explicit:
{:/}

如果有希望的话，我们也可以在大括号里显式声明隐式参数。例如，下面是 `2 ≤ 4` 的 Agda
证明，包括了显式声明了的隐式参数：

{% raw %}<pre class="Agda"><a id="5007" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#5007" class="Function">_</a> <a id="5009" class="Symbol">:</a> <a id="5011" class="Number">2</a> <a id="5013" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="5015" class="Number">4</a>
<a id="5017" class="Symbol">_</a> <a id="5019" class="Symbol">=</a> <a id="5021" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1543" class="InductiveConstructor">s≤s</a> <a id="5025" class="Symbol">{</a><a id="5026" class="Number">1</a><a id="5027" class="Symbol">}</a> <a id="5029" class="Symbol">{</a><a id="5030" class="Number">3</a><a id="5031" class="Symbol">}</a> <a id="5033" class="Symbol">(</a><a id="5034" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="5038" class="Symbol">{</a><a id="5039" class="Number">0</a><a id="5040" class="Symbol">}</a> <a id="5042" class="Symbol">{</a><a id="5043" class="Number">2</a><a id="5044" class="Symbol">}</a> <a id="5046" class="Symbol">(</a><a id="5047" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a> <a id="5051" class="Symbol">{</a><a id="5052" class="Number">2</a><a id="5053" class="Symbol">}))</a>
</pre>{% endraw %}
{::comment}
One may also identify implicit arguments by name:
{:/}

也可以额外加上参数的名字：

{% raw %}<pre class="Agda"><a id="5149" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#5149" class="Function">_</a> <a id="5151" class="Symbol">:</a> <a id="5153" class="Number">2</a> <a id="5155" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="5157" class="Number">4</a>
<a id="5159" class="Symbol">_</a> <a id="5161" class="Symbol">=</a> <a id="5163" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1543" class="InductiveConstructor">s≤s</a> <a id="5167" class="Symbol">{</a><a id="5168" class="Argument">m</a> <a id="5170" class="Symbol">=</a> <a id="5172" class="Number">1</a><a id="5173" class="Symbol">}</a> <a id="5175" class="Symbol">{</a><a id="5176" class="Argument">n</a> <a id="5178" class="Symbol">=</a> <a id="5180" class="Number">3</a><a id="5181" class="Symbol">}</a> <a id="5183" class="Symbol">(</a><a id="5184" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="5188" class="Symbol">{</a><a id="5189" class="Argument">m</a> <a id="5191" class="Symbol">=</a> <a id="5193" class="Number">0</a><a id="5194" class="Symbol">}</a> <a id="5196" class="Symbol">{</a><a id="5197" class="Argument">n</a> <a id="5199" class="Symbol">=</a> <a id="5201" class="Number">2</a><a id="5202" class="Symbol">}</a> <a id="5204" class="Symbol">(</a><a id="5205" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a> <a id="5209" class="Symbol">{</a><a id="5210" class="Argument">n</a> <a id="5212" class="Symbol">=</a> <a id="5214" class="Number">2</a><a id="5215" class="Symbol">}))</a>
</pre>{% endraw %}
{::comment}
In the latter format, you may only supply some implicit arguments:
{:/}

在后者的形式中，也可以只声明一部分隐式参数：

{% raw %}<pre class="Agda"><a id="5337" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#5337" class="Function">_</a> <a id="5339" class="Symbol">:</a> <a id="5341" class="Number">2</a> <a id="5343" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="5345" class="Number">4</a>
<a id="5347" class="Symbol">_</a> <a id="5349" class="Symbol">=</a> <a id="5351" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1543" class="InductiveConstructor">s≤s</a> <a id="5355" class="Symbol">{</a><a id="5356" class="Argument">n</a> <a id="5358" class="Symbol">=</a> <a id="5360" class="Number">3</a><a id="5361" class="Symbol">}</a> <a id="5363" class="Symbol">(</a><a id="5364" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="5368" class="Symbol">{</a><a id="5369" class="Argument">n</a> <a id="5371" class="Symbol">=</a> <a id="5373" class="Number">2</a><a id="5374" class="Symbol">}</a> <a id="5376" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a><a id="5379" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
It is not permitted to swap implicit arguments, even when named.
{:/}

但是不可以改变隐式参数的顺序，即便加上了名字。


{::comment}
## Precedence
{:/}

## 优先级

{::comment}
We declare the precedence for comparison as follows:
{:/}

我们如下定义比较的优先级：

{% raw %}<pre class="Agda"><a id="5625" class="Keyword">infix</a> <a id="5631" class="Number">4</a> <a id="5633" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#1467" class="Datatype Operator">_≤_</a>
</pre>{% endraw %}
{::comment}
We set the precedence of `_≤_` at level 4, so it binds less tightly
than `_+_` at level 6 and hence `1 + 2 ≤ 3` parses as `(1 + 2) ≤ 3`.
We write `infix` to indicate that the operator does not associate to
either the left or right, as it makes no sense to parse `1 ≤ 2 ≤ 3` as
either `(1 ≤ 2) ≤ 3` or `1 ≤ (2 ≤ 3)`.
{:/}

我们将 `_≤_` 的优先级设置为 4，所以它比优先级为 6 的 `_+_` 结合的更紧，此外，
`1 + 2 ≤ 3` 将被解析为 `(1 + 2) ≤ 3`。我们用 `infix` 来表示运算符既不是左结合的，也不是右结合的。因为 `1 ≤ 2 ≤ 3` 解析为 `(1 ≤ 2) ≤ 3` 或者 `1 ≤ (2 ≤ 3)` 都没有意义。


{::comment}
## Decidability
{:/}

## 可决定性

{::comment}
Given two numbers, it is straightforward to compute whether or not the
first is less than or equal to the second.  We don't give the code for
doing so here, but will return to this point in
Chapter [Decidable]({{ site.baseurl }}/Decidable/).
{:/}

给定两个数，我们可以很直接地决定第一个数是不是小于等于第二个数。我们在此处不给出说明的代码，但我们会在 [Decidable]({{ site.baseurl }}/Decidable/) 章节重新讨论这个问题。


{::comment}
## Inversion
{:/}

## 反演

In our definitions, we go from smaller things to larger things.
For instance, from `m ≤ n` we can conclude `suc m ≤ suc n`,
where `suc m` is bigger than `m` (that is, the former contains
the latter), and `suc n` is bigger than `n`. But sometimes we
want to go from bigger things to smaller things.
{:/}

在我们的定义中，我们从更小的东西得到更大的东西。例如，我们可以从
`m ≤ n` 得出 `suc m ≤ suc n` 的结论，这里的 `suc m` 比 `m` 更大
（也就是说，前者包含后者），`suc n` 也比 `n` 更大。但有时我们也需要从更大的东西得到更小的东西。

{::comment}
There is only one way to prove that `suc m ≤ suc n`, for any `m`
and `n`.  This lets us invert our previous rule.
{:/}

只有一种方式能够证明对于任意 `m` 和 `n` 有 `suc m ≤ suc n`。这让我们能够反演（invert）之前的规则。

{% raw %}<pre class="Agda"><a id="inv-s≤s"></a><a id="7252" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#7252" class="Function">inv-s≤s</a> <a id="7260" class="Symbol">:</a> <a id="7262" class="Symbol">∀</a> <a id="7264" class="Symbol">{</a><a id="7265" href="plfa.part1.Relations.html#7265" class="Bound">m</a> <a id="7267" href="plfa.part1.Relations.html#7267" class="Bound">n</a> <a id="7269" class="Symbol">:</a> <a id="7271" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="7272" class="Symbol">}</a>
  <a id="7276" class="Symbol">→</a> <a id="7278" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="7282" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#7265" class="Bound">m</a> <a id="7284" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="7286" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="7290" href="plfa.part1.Relations.html#7267" class="Bound">n</a>
    <a id="7296" class="Comment">-------------</a>
  <a id="7312" class="Symbol">→</a> <a id="7314" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#7265" class="Bound">m</a> <a id="7316" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="7318" href="plfa.part1.Relations.html#7267" class="Bound">n</a>
<a id="7320" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#7252" class="Function">inv-s≤s</a> <a id="7328" class="Symbol">(</a><a id="7329" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="7333" href="plfa.part1.Relations.html#7333" class="Bound">m≤n</a><a id="7336" class="Symbol">)</a> <a id="7338" class="Symbol">=</a> <a id="7340" href="plfa.part1.Relations.html#7333" class="Bound">m≤n</a>
</pre>{% endraw %}
{::comment}
Here `m≤n` (with no spaces) is a variable name while
`m ≤ n` (with spaces) is a type, and the latter
is the type of the former.  It is a common convention
in Agda to derive a variable name by removing
spaces from its type.
{:/}

这里的 `m≤n`（不带空格）是一个变量名，而 `m ≤ n`（带空格）是一个类型，且后者是前者的类型。在 Agda 中，将类型中的空格去掉来作为变量名是一种常见的约定。

{::comment}
Not every rule is invertible; indeed, the rule for `z≤n` has
no non-implicit hypotheses, so there is nothing to invert.
But often inversions of this kind hold.
{:/}

并不是所有规则都可以反演。实际上，`z≤n` 的规则没有非隐式的假设，因此它没有可以被反演的规则。但这种反演通常是成立的。

{::comment}
Another example of inversion is showing that there is
only one way a number can be less than or equal to zero.
{:/}

反演的另一个例子是证明只存在一种情况使得一个数字能够小于或等于零。

{% raw %}<pre class="Agda"><a id="inv-z≤n"></a><a id="8088" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#8088" class="Function">inv-z≤n</a> <a id="8096" class="Symbol">:</a> <a id="8098" class="Symbol">∀</a> <a id="8100" class="Symbol">{</a><a id="8101" href="plfa.part1.Relations.html#8101" class="Bound">m</a> <a id="8103" class="Symbol">:</a> <a id="8105" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="8106" class="Symbol">}</a>
  <a id="8110" class="Symbol">→</a> <a id="8112" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#8101" class="Bound">m</a> <a id="8114" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="8116" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>
    <a id="8125" class="Comment">--------</a>
  <a id="8136" class="Symbol">→</a> <a id="8138" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#8101" class="Bound">m</a> <a id="8140" href="Agda.Builtin.Equality.html#125" class="Datatype Operator">≡</a> <a id="8142" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>
<a id="8147" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#8088" class="Function">inv-z≤n</a> <a id="8155" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a> <a id="8159" class="Symbol">=</a> <a id="8161" href="Agda.Builtin.Equality.html#182" class="InductiveConstructor">refl</a>
</pre>{% endraw %}
{::comment}
## Properties of ordering relations
{:/}

## 序关系的性质

{::comment}
Relations pop up all the time, and mathematicians have agreed
on names for some of the most common properties.

* _Reflexive_. For all `n`, the relation `n ≤ n` holds.
* _Transitive_. For all `m`, `n`, and `p`, if `m ≤ n` and
`n ≤ p` hold, then `m ≤ p` holds.
* _Anti-symmetric_. For all `m` and `n`, if both `m ≤ n` and
`n ≤ m` hold, then `m ≡ n` holds.
* _Total_. For all `m` and `n`, either `m ≤ n` or `n ≤ m`
holds.
{:/}

数学家对于关系的常见性质给出了约定的名称。

* **自反（Reflexive）**：对于所有的 `n`，关系 `n ≤ n` 成立。
* **传递（Transitive）**：对于所有的 `m`、 `n` 和 `p`，如果 `m ≤ n` 和 `n ≤ p`
  成立，那么 `m ≤ p` 也成立。
* **反对称（Anti-symmetric）**：对于所有的 `m` 和 `n`，如果 `m ≤ n` 和 `n ≤ m`
  同时成立，那么 `m ≡ n` 成立。
* **完全（Total）**：对于所有的 `m` 和 `n`，`m ≤ n` 或者 `n ≤ m` 成立。

{::comment}
The relation `_≤_` satisfies all four of these properties.
{:/}

`_≤_` 关系满足上述四条性质。

{::comment}
There are also names for some combinations of these properties.

* _Preorder_. Any relation that is reflexive and transitive.
* _Partial order_. Any preorder that is also anti-symmetric.
* _Total order_. Any partial order that is also total.
{:/}

对于上述性质的组合也有约定的名称。

* **预序（Preorder）**：满足自反和传递的关系。
* **偏序（Partial Order）**：满足反对称的预序。
* **全序（Total Order）**：满足完全的偏序。

{::comment}
If you ever bump into a relation at a party, you now know how
to make small talk, by asking it whether it is reflexive, transitive,
anti-symmetric, and total. Or instead you might ask whether it is a
preorder, partial order, or total order.
{:/}

如果你进入了关于关系的聚会，你现在知道怎么样和人讨论了，可以讨论关于自反、传递、反对称和完全，或者问一问这是不是预序、偏序或者全序。

{::comment}
Less frivolously, if you ever bump into a relation while reading a
technical paper, this gives you a way to orient yourself, by checking
whether or not it is a preorder, partial order, or total order.  A
careful author will often call out these properties---or their
lack---for instance by saying that a newly introduced relation is a
partial order but not a total order.
{:/}

更认真的来说，如果你在阅读论文时碰到了一个关系，本文的介绍让你可以对关系有基本的了解和判断，来判断这个关系是不是预序、偏序或者全序。一个认真的作者一般会在文章指出这个关系具有（或者缺少）
上述性质，比如说指出新定义的关系是一个偏序而不是全序。

{::comment}
#### Exercise `orderings` (practice) {#orderings}
{:/}

#### 练习 `orderings`（实践） {#orderings}

{::comment}
Give an example of a preorder that is not a partial order.
{:/}

给出一个不是偏序的预序的例子。

{::comment}
{% raw %}<pre class="Agda"><a id="10497" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="10534" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}
{::comment}
Give an example of a partial order that is not a total order.
{:/}

给出一个不是全序的偏序的例子。

{::comment}
{% raw %}<pre class="Agda"><a id="10665" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="10702" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}

{::comment}
## Reflexivity
{:/}

## 自反性

{::comment}
The first property to prove about comparison is that it is reflexive:
for any natural `n`, the relation `n ≤ n` holds.  We follow the
convention in the standard library and make the argument implicit,
as that will make it easier to invoke reflexivity:
{:/}

我们第一个来证明的性质是自反性：对于任意自然数 `n`，关系 `n ≤ n` 成立。我们使用标准库的惯例来隐式申明参数，在使用自反性的证明时这样可以更加方便。

{% raw %}<pre class="Agda"><a id="≤-refl"></a><a id="11118" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#11118" class="Function">≤-refl</a> <a id="11125" class="Symbol">:</a> <a id="11127" class="Symbol">∀</a> <a id="11129" class="Symbol">{</a><a id="11130" href="plfa.part1.Relations.html#11130" class="Bound">n</a> <a id="11132" class="Symbol">:</a> <a id="11134" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="11135" class="Symbol">}</a>
    <a id="11141" class="Comment">-----</a>
  <a id="11149" class="Symbol">→</a> <a id="11151" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#11130" class="Bound">n</a> <a id="11153" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="11155" href="plfa.part1.Relations.html#11130" class="Bound">n</a>
<a id="11157" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#11118" class="Function">≤-refl</a> <a id="11164" class="Symbol">{</a><a id="11165" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a><a id="11169" class="Symbol">}</a> <a id="11171" class="Symbol">=</a> <a id="11173" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>
<a id="11177" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#11118" class="Function">≤-refl</a> <a id="11184" class="Symbol">{</a><a id="11185" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="11189" href="plfa.part1.Relations.html#11189" class="Bound">n</a><a id="11190" class="Symbol">}</a> <a id="11192" class="Symbol">=</a> <a id="11194" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="11198" href="plfa.part1.Relations.html#11118" class="Function">≤-refl</a>
</pre>{% endraw %}
{::comment}
The proof is a straightforward induction on the implicit argument `n`.
In the base case, `zero ≤ zero` holds by `z≤n`.  In the inductive
case, the inductive hypothesis `≤-refl {n}` gives us a proof of `n ≤
n`, and applying `s≤s` to that yields a proof of `suc n ≤ suc n`.
{:/}

这个证明直接在 `n` 上进行归纳。在起始步骤中，`zero ≤ zero` 由 `z≤n` 证明；在归纳步骤中，归纳假设 `≤-refl {n}` 给我们带来了 `n ≤ n` 的证明，我们只需要使用 `s≤s`，就可以获得
`suc n ≤ suc n` 的证明。

{::comment}
It is a good exercise to prove reflexivity interactively in Emacs,
using holes and the `C-c C-c`, `C-c C-,`, and `C-c C-r` commands.
{:/}

在 Emacs 中来交互式地证明自反性是一个很好的练习，可以使用洞，以及 `C-c C-c`、
`C-c C-,` 和 `C-c C-r` 命令。


{::comment}
## Transitivity
{:/}

## 传递性

{::comment}
The second property to prove about comparison is that it is
transitive: for any naturals `m`, `n`, and `p`, if `m ≤ n` and `n ≤ p`
hold, then `m ≤ p` holds.  Again, `m`, `n`, and `p` are implicit:
{:/}

我们第二个证明的性质是传递性：对于任意自然数 `m` 和 `n`，如果 `m ≤ n` 和 `n ≤ p`
成立，那么 `m ≤ p` 成立。同样，`m`、`n` 和 `p` 是隐式参数：

{% raw %}<pre class="Agda"><a id="≤-trans"></a><a id="12221" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#12221" class="Function">≤-trans</a> <a id="12229" class="Symbol">:</a> <a id="12231" class="Symbol">∀</a> <a id="12233" class="Symbol">{</a><a id="12234" href="plfa.part1.Relations.html#12234" class="Bound">m</a> <a id="12236" href="plfa.part1.Relations.html#12236" class="Bound">n</a> <a id="12238" href="plfa.part1.Relations.html#12238" class="Bound">p</a> <a id="12240" class="Symbol">:</a> <a id="12242" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="12243" class="Symbol">}</a>
  <a id="12247" class="Symbol">→</a> <a id="12249" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#12234" class="Bound">m</a> <a id="12251" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="12253" href="plfa.part1.Relations.html#12236" class="Bound">n</a>
  <a id="12257" class="Symbol">→</a> <a id="12259" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#12236" class="Bound">n</a> <a id="12261" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="12263" href="plfa.part1.Relations.html#12238" class="Bound">p</a>
    <a id="12269" class="Comment">-----</a>
  <a id="12277" class="Symbol">→</a> <a id="12279" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#12234" class="Bound">m</a> <a id="12281" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="12283" href="plfa.part1.Relations.html#12238" class="Bound">p</a>
<a id="12285" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#12221" class="Function">≤-trans</a> <a id="12293" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>       <a id="12303" class="Symbol">_</a>          <a id="12314" class="Symbol">=</a>  <a id="12317" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>
<a id="12321" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#12221" class="Function">≤-trans</a> <a id="12329" class="Symbol">(</a><a id="12330" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="12334" href="plfa.part1.Relations.html#12334" class="Bound">m≤n</a><a id="12337" class="Symbol">)</a> <a id="12339" class="Symbol">(</a><a id="12340" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="12344" href="plfa.part1.Relations.html#12344" class="Bound">n≤p</a><a id="12347" class="Symbol">)</a>  <a id="12350" class="Symbol">=</a>  <a id="12353" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="12357" class="Symbol">(</a><a id="12358" href="plfa.part1.Relations.html#12221" class="Function">≤-trans</a> <a id="12366" href="plfa.part1.Relations.html#12334" class="Bound">m≤n</a> <a id="12370" href="plfa.part1.Relations.html#12344" class="Bound">n≤p</a><a id="12373" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
Here the proof is by induction on the _evidence_ that `m ≤ n`.  In the
base case, the first inequality holds by `z≤n` and must show `zero ≤
p`, which follows immediately by `z≤n`.  In this case, the fact that
`n ≤ p` is irrelevant, and we write `_` as the pattern to indicate
that the corresponding evidence is unused.
{:/}

这里我们在 `m ≤ n` 的**证据（Evidence）**上进行归纳。在起始步骤里，第一个不等式因为 `z≤n` 而成立，那么结论亦可由 `z≤n` 而得出。在这里，`n ≤ p` 的证明是不需要的，我们用 `_` 来表示这个证明没有被使用。

{::comment}
In the inductive case, the first inequality holds by `s≤s m≤n`
and the second inequality by `s≤s n≤p`, and so we are given
`suc m ≤ suc n` and `suc n ≤ suc p`, and must show `suc m ≤ suc p`.
The inductive hypothesis `≤-trans m≤n n≤p` establishes
that `m ≤ p`, and our goal follows by applying `s≤s`.
{:/}

在归纳步骤中，第一个不等式因为 `s≤s m≤n` 而成立，第二个不等式因为 `s≤s n≤p` 而成立，所以我们已知 `suc m ≤ suc n` 和 `suc n ≤ suc p`，求证 `suc m ≤ suc p`。通过归纳假设 `≤-trans m≤n n≤p`，我们得知 `m ≤ p`，在此之上使用 `s≤s` 即可证。

{::comment}
The case `≤-trans (s≤s m≤n) z≤n` cannot arise, since the first
inequality implies the middle value is `suc n` while the second
inequality implies that it is `zero`.  Agda can determine that such a
case cannot arise, and does not require (or permit) it to be listed.
{:/}

`≤-trans (s≤s m≤n) z≤n` 不可能发生，因为第一个不等式告诉我们中间的数是一个 `suc n`，而第二个不等式告诉我们中间的书是 `zero`。Agda 可以推断这样的情况不可能发现，所以我们不需要
（也不可以）列出这种情况。

{::comment}
Alternatively, we could make the implicit parameters explicit:
{:/}

我们也可以将隐式参数显式地声明。

{% raw %}<pre class="Agda"><a id="≤-trans′"></a><a id="13847" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#13847" class="Function">≤-trans′</a> <a id="13856" class="Symbol">:</a> <a id="13858" class="Symbol">∀</a> <a id="13860" class="Symbol">(</a><a id="13861" href="plfa.part1.Relations.html#13861" class="Bound">m</a> <a id="13863" href="plfa.part1.Relations.html#13863" class="Bound">n</a> <a id="13865" href="plfa.part1.Relations.html#13865" class="Bound">p</a> <a id="13867" class="Symbol">:</a> <a id="13869" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="13870" class="Symbol">)</a>
  <a id="13874" class="Symbol">→</a> <a id="13876" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#13861" class="Bound">m</a> <a id="13878" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="13880" href="plfa.part1.Relations.html#13863" class="Bound">n</a>
  <a id="13884" class="Symbol">→</a> <a id="13886" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#13863" class="Bound">n</a> <a id="13888" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="13890" href="plfa.part1.Relations.html#13865" class="Bound">p</a>
    <a id="13896" class="Comment">-----</a>
  <a id="13904" class="Symbol">→</a> <a id="13906" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#13861" class="Bound">m</a> <a id="13908" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="13910" href="plfa.part1.Relations.html#13865" class="Bound">p</a>
<a id="13912" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#13847" class="Function">≤-trans′</a> <a id="13921" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>    <a id="13929" class="Symbol">_</a>       <a id="13937" class="Symbol">_</a>       <a id="13945" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>       <a id="13955" class="Symbol">_</a>          <a id="13966" class="Symbol">=</a>  <a id="13969" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>
<a id="13973" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#13847" class="Function">≤-trans′</a> <a id="13982" class="Symbol">(</a><a id="13983" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="13987" href="plfa.part1.Relations.html#13987" class="Bound">m</a><a id="13988" class="Symbol">)</a> <a id="13990" class="Symbol">(</a><a id="13991" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="13995" href="plfa.part1.Relations.html#13995" class="Bound">n</a><a id="13996" class="Symbol">)</a> <a id="13998" class="Symbol">(</a><a id="13999" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="14003" href="plfa.part1.Relations.html#14003" class="Bound">p</a><a id="14004" class="Symbol">)</a> <a id="14006" class="Symbol">(</a><a id="14007" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="14011" href="plfa.part1.Relations.html#14011" class="Bound">m≤n</a><a id="14014" class="Symbol">)</a> <a id="14016" class="Symbol">(</a><a id="14017" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="14021" href="plfa.part1.Relations.html#14021" class="Bound">n≤p</a><a id="14024" class="Symbol">)</a>  <a id="14027" class="Symbol">=</a>  <a id="14030" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="14034" class="Symbol">(</a><a id="14035" href="plfa.part1.Relations.html#13847" class="Function">≤-trans′</a> <a id="14044" href="plfa.part1.Relations.html#13987" class="Bound">m</a> <a id="14046" href="plfa.part1.Relations.html#13995" class="Bound">n</a> <a id="14048" href="plfa.part1.Relations.html#14003" class="Bound">p</a> <a id="14050" href="plfa.part1.Relations.html#14011" class="Bound">m≤n</a> <a id="14054" href="plfa.part1.Relations.html#14021" class="Bound">n≤p</a><a id="14057" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
One might argue that this is clearer or one might argue that the extra
length obscures the essence of the proof.  We will usually opt for
shorter proofs.
{:/}

有人说这样的证明更加的清晰，也有人说这个更长的证明让人难以抓住证明的重点。我们一般选择使用简短的证明。

{::comment}
The technique of induction on evidence that a property holds (e.g.,
inducting on evidence that `m ≤ n`)---rather than induction on
values of which the property holds (e.g., inducting on `m`)---will turn
out to be immensely valuable, and one that we use often.
{:/}

对于性质成立证明进行的归纳（如上文中对于 `m ≤ n` 的证明进行归纳），相比于对于性质成立的值进行的归纳
（如对于 `m` 进行归纳），有非常大的价值。我们会经常使用这样的方法。

{::comment}
Again, it is a good exercise to prove transitivity interactively in Emacs,
using holes and the `C-c C-c`, `C-c C-,`, and `C-c C-r` commands.
{:/}

同样，在 Emacs 中来交互式地证明传递性是一个很好的练习，可以使用洞，以及 `C-c C-c`、
`C-c C-,` 和 `C-c C-r` 命令。


{::comment}
## Anti-symmetry
{:/}

## 反对称性

{::comment}
The third property to prove about comparison is that it is
antisymmetric: for all naturals `m` and `n`, if both `m ≤ n` and `n ≤
m` hold, then `m ≡ n` holds:
{:/}

我们证明的第三个性质是反对称性：对于所有的自然数 `m` 和 `n`，如果 `m ≤ n` 和 `n ≤ m`
同时成立，那么 `m ≡ n` 成立：

{% raw %}<pre class="Agda"><a id="≤-antisym"></a><a id="15200" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#15200" class="Function">≤-antisym</a> <a id="15210" class="Symbol">:</a> <a id="15212" class="Symbol">∀</a> <a id="15214" class="Symbol">{</a><a id="15215" href="plfa.part1.Relations.html#15215" class="Bound">m</a> <a id="15217" href="plfa.part1.Relations.html#15217" class="Bound">n</a> <a id="15219" class="Symbol">:</a> <a id="15221" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="15222" class="Symbol">}</a>
  <a id="15226" class="Symbol">→</a> <a id="15228" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#15215" class="Bound">m</a> <a id="15230" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="15232" href="plfa.part1.Relations.html#15217" class="Bound">n</a>
  <a id="15236" class="Symbol">→</a> <a id="15238" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#15217" class="Bound">n</a> <a id="15240" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="15242" href="plfa.part1.Relations.html#15215" class="Bound">m</a>
    <a id="15248" class="Comment">-----</a>
  <a id="15256" class="Symbol">→</a> <a id="15258" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#15215" class="Bound">m</a> <a id="15260" href="Agda.Builtin.Equality.html#125" class="Datatype Operator">≡</a> <a id="15262" href="plfa.part1.Relations.html#15217" class="Bound">n</a>
<a id="15264" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#15200" class="Function">≤-antisym</a> <a id="15274" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>       <a id="15284" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>        <a id="15295" class="Symbol">=</a>  <a id="15298" href="Agda.Builtin.Equality.html#182" class="InductiveConstructor">refl</a>
<a id="15303" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#15200" class="Function">≤-antisym</a> <a id="15313" class="Symbol">(</a><a id="15314" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="15318" href="plfa.part1.Relations.html#15318" class="Bound">m≤n</a><a id="15321" class="Symbol">)</a> <a id="15323" class="Symbol">(</a><a id="15324" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="15328" href="plfa.part1.Relations.html#15328" class="Bound">n≤m</a><a id="15331" class="Symbol">)</a>  <a id="15334" class="Symbol">=</a>  <a id="15337" href="https://agda.github.io/agda-stdlib/v1.1/Relation.Binary.PropositionalEquality.Core.html#1090" class="Function">cong</a> <a id="15342" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="15346" class="Symbol">(</a><a id="15347" href="plfa.part1.Relations.html#15200" class="Function">≤-antisym</a> <a id="15357" href="plfa.part1.Relations.html#15318" class="Bound">m≤n</a> <a id="15361" href="plfa.part1.Relations.html#15328" class="Bound">n≤m</a><a id="15364" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
Again, the proof is by induction over the evidence that `m ≤ n`
and `n ≤ m` hold.
{:/}

同样，我们对于 `m ≤ n` 和 `n ≤ m` 的证明进行归纳。

{::comment}
In the base case, both inequalities hold by `z≤n`, and so we are given
`zero ≤ zero` and `zero ≤ zero` and must show `zero ≡ zero`, which
follows by reflexivity.  (Reflexivity of equality, that is, not
reflexivity of inequality.)
{:/}

在起始步骤中，两个不等式都因为 `z≤n` 而成立。因此我们已知 `zero ≤ zero` 和 `zero ≤ zero`，求证 `zero ≡ zero`，由自反性可证。（注：由等式的自反性可证，而不是不等式的自反性）

{::comment}
In the inductive case, the first inequality holds by `s≤s m≤n` and the
second inequality holds by `s≤s n≤m`, and so we are given `suc m ≤ suc n`
and `suc n ≤ suc m` and must show `suc m ≡ suc n`.  The inductive
hypothesis `≤-antisym m≤n n≤m` establishes that `m ≡ n`, and our goal
follows by congruence.
{::comment}

在归纳步骤中，第一个不等式因为 `s≤s m≤n` 而成立，第二个等式因为 `s≤s n≤m` 而成立。因此我们已知
`suc m ≤ suc n` 和 `suc n ≤ suc m`，求证 `suc m ≡ suc n`。归纳假设 `≤-antisym m≤n n≤m`
可以证明 `m ≡ n`，因此我们可以使用同余性完成证明。


{::comment}
#### Exercise `≤-antisym-cases` (practice) {#leq-antisym-cases}
{:/}

#### 练习 `≤-antisym-cases`（实践） {#leq-antisym-cases}

{::comment}
The above proof omits cases where one argument is `z≤n` and one
argument is `s≤s`.  Why is it ok to omit them?
{:/}

上面的证明中省略了一个参数是 `z≤n`，另一个参数是 `s≤s` 的情况。为什么可以省略这种情况？

{::comment}
{% raw %}<pre class="Agda"><a id="16698" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="16735" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}

{::comment}
## Total
{:/}

## 完全性

{::comment}
The fourth property to prove about comparison is that it is total:
for any naturals `m` and `n` either `m ≤ n` or `n ≤ m`, or both if
`m` and `n` are equal.
{:/}

我们证明的第四个性质是完全性：对于任何自然数 `m` 和 `n`，`m ≤ n` 或者 `n ≤ m` 成立。在 `m` 和 `n` 相等时，两者同时成立。

{::comment}
We specify what it means for inequality to be total:
{:/}

我们首先来说明怎么样不等式才是完全的：

{% raw %}<pre class="Agda"><a id="17141" class="Keyword">data</a> <a id="Total"></a><a id="17146" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17146" class="Datatype">Total</a> <a id="17152" class="Symbol">(</a><a id="17153" href="plfa.part1.Relations.html#17153" class="Bound">m</a> <a id="17155" href="plfa.part1.Relations.html#17155" class="Bound">n</a> <a id="17157" class="Symbol">:</a> <a id="17159" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="17160" class="Symbol">)</a> <a id="17162" class="Symbol">:</a> <a id="17164" class="PrimitiveType">Set</a> <a id="17168" class="Keyword">where</a>

  <a id="Total.forward"></a><a id="17177" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17177" class="InductiveConstructor">forward</a> <a id="17185" class="Symbol">:</a>
      <a id="17193" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17153" class="Bound">m</a> <a id="17195" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="17197" href="plfa.part1.Relations.html#17155" class="Bound">n</a>
      <a id="17205" class="Comment">---------</a>
    <a id="17219" class="Symbol">→</a> <a id="17221" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17146" class="Datatype">Total</a> <a id="17227" href="plfa.part1.Relations.html#17153" class="Bound">m</a> <a id="17229" href="plfa.part1.Relations.html#17155" class="Bound">n</a>

  <a id="Total.flipped"></a><a id="17234" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17234" class="InductiveConstructor">flipped</a> <a id="17242" class="Symbol">:</a>
      <a id="17250" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17155" class="Bound">n</a> <a id="17252" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="17254" href="plfa.part1.Relations.html#17153" class="Bound">m</a>
      <a id="17262" class="Comment">---------</a>
    <a id="17276" class="Symbol">→</a> <a id="17278" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17146" class="Datatype">Total</a> <a id="17284" href="plfa.part1.Relations.html#17153" class="Bound">m</a> <a id="17286" href="plfa.part1.Relations.html#17155" class="Bound">n</a>
</pre>{% endraw %}
{::comment}
Evidence that `Total m n` holds is either of the form
`forward m≤n` or `flipped n≤m`, where `m≤n` and `n≤m` are
evidence of `m ≤ n` and `n ≤ m` respectively.
{:/}

`Total m n` 成立的证明有两种形式：`forward m≤n` 或者 `flipped n≤m`，其中
`m≤n` 和 `n≤m` 分别是 `m ≤ n` 和 `n ≤ m` 的证明。

{::comment}
(For those familiar with logic, the above definition
could also be written as a disjunction. Disjunctions will
be introduced in Chapter [Connectives]({{ site.baseurl }}/Connectives/).)
{:/}

（如果你对于逻辑学有所了解，上面的定义可以由析取（Disjunction）表示。我们会在 [Connectives]({{ site.baseurl }}/Connectives/) 章节介绍析取。）

{::comment}
This is our first use of a datatype with _parameters_,
in this case `m` and `n`.  It is equivalent to the following
indexed datatype:
{:/}

这是我们第一次使用带*参数*的数据类型，这里 `m` 和 `n` 是参数。这等同于下面的索引数据类型：

{% raw %}<pre class="Agda"><a id="18083" class="Keyword">data</a> <a id="Total′"></a><a id="18088" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#18088" class="Datatype">Total′</a> <a id="18095" class="Symbol">:</a> <a id="18097" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a> <a id="18099" class="Symbol">→</a> <a id="18101" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a> <a id="18103" class="Symbol">→</a> <a id="18105" class="PrimitiveType">Set</a> <a id="18109" class="Keyword">where</a>

  <a id="Total′.forward′"></a><a id="18118" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#18118" class="InductiveConstructor">forward′</a> <a id="18127" class="Symbol">:</a> <a id="18129" class="Symbol">∀</a> <a id="18131" class="Symbol">{</a><a id="18132" href="plfa.part1.Relations.html#18132" class="Bound">m</a> <a id="18134" href="plfa.part1.Relations.html#18134" class="Bound">n</a> <a id="18136" class="Symbol">:</a> <a id="18138" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="18139" class="Symbol">}</a>
    <a id="18145" class="Symbol">→</a> <a id="18147" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#18132" class="Bound">m</a> <a id="18149" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="18151" href="plfa.part1.Relations.html#18134" class="Bound">n</a>
      <a id="18159" class="Comment">----------</a>
    <a id="18174" class="Symbol">→</a> <a id="18176" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#18088" class="Datatype">Total′</a> <a id="18183" href="plfa.part1.Relations.html#18132" class="Bound">m</a> <a id="18185" href="plfa.part1.Relations.html#18134" class="Bound">n</a>

  <a id="Total′.flipped′"></a><a id="18190" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#18190" class="InductiveConstructor">flipped′</a> <a id="18199" class="Symbol">:</a> <a id="18201" class="Symbol">∀</a> <a id="18203" class="Symbol">{</a><a id="18204" href="plfa.part1.Relations.html#18204" class="Bound">m</a> <a id="18206" href="plfa.part1.Relations.html#18206" class="Bound">n</a> <a id="18208" class="Symbol">:</a> <a id="18210" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="18211" class="Symbol">}</a>
    <a id="18217" class="Symbol">→</a> <a id="18219" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#18206" class="Bound">n</a> <a id="18221" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="18223" href="plfa.part1.Relations.html#18204" class="Bound">m</a>
      <a id="18231" class="Comment">----------</a>
    <a id="18246" class="Symbol">→</a> <a id="18248" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#18088" class="Datatype">Total′</a> <a id="18255" href="plfa.part1.Relations.html#18204" class="Bound">m</a> <a id="18257" href="plfa.part1.Relations.html#18206" class="Bound">n</a>
</pre>{% endraw %}
{::comment}
Each parameter of the type translates as an implicit parameter of each
constructor.  Unlike an indexed datatype, where the indexes can vary
(as in `zero ≤ n` and `suc m ≤ suc n`), in a parameterised datatype
the parameters must always be the same (as in `Total m n`).
Parameterised declarations are shorter, easier to read, and
occasionally aid Agda's termination checker, so we will use them in
preference to indexed types when possible.
{:/}

类型里的每个参数都转换成构造子的一个隐式参数。索引数据类型中的索引可以变化，正如在
`zero ≤ n` 和 `suc m ≤ suc n` 中那样，而参数化数据类型不一样，其参数必须保持相同，正如在 `Total m n` 中那样。参数化的声明更短，更易于阅读，而且有时可以帮助到 Agda 的终结检查器，所以我们尽可能地使用它们，而不是索引数据类型。

{::comment}
With that preliminary out of the way, we specify and prove totality:
{:/}

在上述准备工作完成后，我们定义并证明完全性。

{% raw %}<pre class="Agda"><a id="≤-total"></a><a id="19017" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#19017" class="Function">≤-total</a> <a id="19025" class="Symbol">:</a> <a id="19027" class="Symbol">∀</a> <a id="19029" class="Symbol">(</a><a id="19030" href="plfa.part1.Relations.html#19030" class="Bound">m</a> <a id="19032" href="plfa.part1.Relations.html#19032" class="Bound">n</a> <a id="19034" class="Symbol">:</a> <a id="19036" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="19037" class="Symbol">)</a> <a id="19039" class="Symbol">→</a> <a id="19041" href="plfa.part1.Relations.html#17146" class="Datatype">Total</a> <a id="19047" href="plfa.part1.Relations.html#19030" class="Bound">m</a> <a id="19049" href="plfa.part1.Relations.html#19032" class="Bound">n</a>
<a id="19051" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#19017" class="Function">≤-total</a> <a id="19059" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>    <a id="19067" href="plfa.part1.Relations.html#19067" class="Bound">n</a>                         <a id="19093" class="Symbol">=</a>  <a id="19096" href="plfa.part1.Relations.html#17177" class="InductiveConstructor">forward</a> <a id="19104" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>
<a id="19108" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#19017" class="Function">≤-total</a> <a id="19116" class="Symbol">(</a><a id="19117" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="19121" href="plfa.part1.Relations.html#19121" class="Bound">m</a><a id="19122" class="Symbol">)</a> <a id="19124" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>                      <a id="19150" class="Symbol">=</a>  <a id="19153" href="plfa.part1.Relations.html#17234" class="InductiveConstructor">flipped</a> <a id="19161" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>
<a id="19165" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#19017" class="Function">≤-total</a> <a id="19173" class="Symbol">(</a><a id="19174" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="19178" href="plfa.part1.Relations.html#19178" class="Bound">m</a><a id="19179" class="Symbol">)</a> <a id="19181" class="Symbol">(</a><a id="19182" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="19186" href="plfa.part1.Relations.html#19186" class="Bound">n</a><a id="19187" class="Symbol">)</a> <a id="19189" class="Keyword">with</a> <a id="19194" href="plfa.part1.Relations.html#19017" class="Function">≤-total</a> <a id="19202" href="plfa.part1.Relations.html#19178" class="Bound">m</a> <a id="19204" href="plfa.part1.Relations.html#19186" class="Bound">n</a>
<a id="19206" class="Symbol">...</a>                        <a id="19233" class="Symbol">|</a> <a id="19235" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17177" class="InductiveConstructor">forward</a> <a id="19243" href="plfa.part1.Relations.html#19243" class="Bound">m≤n</a>  <a id="19248" class="Symbol">=</a>  <a id="19251" href="plfa.part1.Relations.html#17177" class="InductiveConstructor">forward</a> <a id="19259" class="Symbol">(</a><a id="19260" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="19264" href="plfa.part1.Relations.html#19243" class="Bound">m≤n</a><a id="19267" class="Symbol">)</a>
<a id="19269" class="Symbol">...</a>                        <a id="19296" class="Symbol">|</a> <a id="19298" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17234" class="InductiveConstructor">flipped</a> <a id="19306" href="plfa.part1.Relations.html#19306" class="Bound">n≤m</a>  <a id="19311" class="Symbol">=</a>  <a id="19314" href="plfa.part1.Relations.html#17234" class="InductiveConstructor">flipped</a> <a id="19322" class="Symbol">(</a><a id="19323" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="19327" href="plfa.part1.Relations.html#19306" class="Bound">n≤m</a><a id="19330" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
In this case the proof is by induction over both the first
and second arguments.  We perform a case analysis:

* _First base case_: If the first argument is `zero` and the
  second argument is `n` then the forward case holds,
  with `z≤n` as evidence that `zero ≤ n`.

* _Second base case_: If the first argument is `suc m` and the
  second argument is `zero` then the flipped case holds, with
  `z≤n` as evidence that `zero ≤ suc m`.

* _Inductive case_: If the first argument is `suc m` and the
  second argument is `suc n`, then the inductive hypothesis
  `≤-total m n` establishes one of the following:

  + The forward case of the inductive hypothesis holds with `m≤n` as
    evidence that `m ≤ n`, from which it follows that the forward case of the
    proposition holds with `s≤s m≤n` as evidence that `suc m ≤ suc n`.

  + The flipped case of the inductive hypothesis holds with `n≤m` as
    evidence that `n ≤ m`, from which it follows that the flipped case of the
    proposition holds with `s≤s n≤m` as evidence that `suc n ≤ suc m`.
{:/}

这里，我们的证明在两个参数上进行归纳，并按照情况分析：

* **第一起始步骤**：如果第一个参数是 `zero`，第二个参数是 `n`，那么 forward
  条件成立，我们使用 `z≤n` 作为 `zero ≤ n` 的证明。

* **第二起始步骤**：如果第一个参数是 `suc m`，第二个参数是 `zero`，那么 flipped
  条件成立，我们使用 `z≤n` 作为 `zero ≤ suc m` 的证明。

* **归纳步骤**：如果第一个参数是 `suc m`，第二个参数是 `suc n`，那么归纳假设
  `≤-total m n` 可以给出如下推断：

  + 归纳假设的 forward 条件成立，以 `m≤n` 作为 `m ≤ n` 的证明。以此我们可以使用
    `s≤s m≤n` 作为 `suc m ≤ suc n` 来证明 forward 条件成立。

  + 归纳假设的 flipped 条件成立，以 `n≤m` 作为 `n ≤ m` 的证明。以此我们可以使用
    `s≤s n≤m` 作为 `suc n ≤ suc m` 来证明 flipped 条件成立。

{::comment}
This is our first use of the `with` clause in Agda.  The keyword
`with` is followed by an expression and one or more subsequent lines.
Each line begins with an ellipsis (`...`) and a vertical bar (`|`),
followed by a pattern to be matched against the expression
and the right-hand side of the equation.
{:/}

这是我们第一次在 Agda 中使用 `with` 语句。`with` 关键字后面有一个表达式和一或多行。每行以省略号（`...`）和一个竖线（`|`）开头，后面跟着用来匹配表达式的模式，和等式的右手边。

{::comment}
Every use of `with` is equivalent to defining a helper function.  For
example, the definition above is equivalent to the following:
{:/}

使用 `with` 语句等同于定义一个辅助函数。比如说，上面的定义和下面的等价：

{% raw %}<pre class="Agda"><a id="≤-total′"></a><a id="21527" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#21527" class="Function">≤-total′</a> <a id="21536" class="Symbol">:</a> <a id="21538" class="Symbol">∀</a> <a id="21540" class="Symbol">(</a><a id="21541" href="plfa.part1.Relations.html#21541" class="Bound">m</a> <a id="21543" href="plfa.part1.Relations.html#21543" class="Bound">n</a> <a id="21545" class="Symbol">:</a> <a id="21547" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="21548" class="Symbol">)</a> <a id="21550" class="Symbol">→</a> <a id="21552" href="plfa.part1.Relations.html#17146" class="Datatype">Total</a> <a id="21558" href="plfa.part1.Relations.html#21541" class="Bound">m</a> <a id="21560" href="plfa.part1.Relations.html#21543" class="Bound">n</a>
<a id="21562" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#21527" class="Function">≤-total′</a> <a id="21571" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>    <a id="21579" href="plfa.part1.Relations.html#21579" class="Bound">n</a>        <a id="21588" class="Symbol">=</a>  <a id="21591" href="plfa.part1.Relations.html#17177" class="InductiveConstructor">forward</a> <a id="21599" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>
<a id="21603" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#21527" class="Function">≤-total′</a> <a id="21612" class="Symbol">(</a><a id="21613" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="21617" href="plfa.part1.Relations.html#21617" class="Bound">m</a><a id="21618" class="Symbol">)</a> <a id="21620" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>     <a id="21629" class="Symbol">=</a>  <a id="21632" href="plfa.part1.Relations.html#17234" class="InductiveConstructor">flipped</a> <a id="21640" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>
<a id="21644" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#21527" class="Function">≤-total′</a> <a id="21653" class="Symbol">(</a><a id="21654" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="21658" href="plfa.part1.Relations.html#21658" class="Bound">m</a><a id="21659" class="Symbol">)</a> <a id="21661" class="Symbol">(</a><a id="21662" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="21666" href="plfa.part1.Relations.html#21666" class="Bound">n</a><a id="21667" class="Symbol">)</a>  <a id="21670" class="Symbol">=</a>  <a id="21673" href="plfa.part1.Relations.html#21705" class="Function">helper</a> <a id="21680" class="Symbol">(</a><a id="21681" href="plfa.part1.Relations.html#21527" class="Function">≤-total′</a> <a id="21690" href="plfa.part1.Relations.html#21658" class="Bound">m</a> <a id="21692" href="plfa.part1.Relations.html#21666" class="Bound">n</a><a id="21693" class="Symbol">)</a>
  <a id="21697" class="Keyword">where</a>
  <a id="21705" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#21705" class="Function">helper</a> <a id="21712" class="Symbol">:</a> <a id="21714" href="plfa.part1.Relations.html#17146" class="Datatype">Total</a> <a id="21720" href="plfa.part1.Relations.html#21658" class="Bound">m</a> <a id="21722" href="plfa.part1.Relations.html#21666" class="Bound">n</a> <a id="21724" class="Symbol">→</a> <a id="21726" href="plfa.part1.Relations.html#17146" class="Datatype">Total</a> <a id="21732" class="Symbol">(</a><a id="21733" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="21737" href="plfa.part1.Relations.html#21658" class="Bound">m</a><a id="21738" class="Symbol">)</a> <a id="21740" class="Symbol">(</a><a id="21741" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="21745" href="plfa.part1.Relations.html#21666" class="Bound">n</a><a id="21746" class="Symbol">)</a>
  <a id="21750" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#21705" class="Function">helper</a> <a id="21757" class="Symbol">(</a><a id="21758" href="plfa.part1.Relations.html#17177" class="InductiveConstructor">forward</a> <a id="21766" href="plfa.part1.Relations.html#21766" class="Bound">m≤n</a><a id="21769" class="Symbol">)</a>  <a id="21772" class="Symbol">=</a>  <a id="21775" href="plfa.part1.Relations.html#17177" class="InductiveConstructor">forward</a> <a id="21783" class="Symbol">(</a><a id="21784" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="21788" href="plfa.part1.Relations.html#21766" class="Bound">m≤n</a><a id="21791" class="Symbol">)</a>
  <a id="21795" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#21705" class="Function">helper</a> <a id="21802" class="Symbol">(</a><a id="21803" href="plfa.part1.Relations.html#17234" class="InductiveConstructor">flipped</a> <a id="21811" href="plfa.part1.Relations.html#21811" class="Bound">n≤m</a><a id="21814" class="Symbol">)</a>  <a id="21817" class="Symbol">=</a>  <a id="21820" href="plfa.part1.Relations.html#17234" class="InductiveConstructor">flipped</a> <a id="21828" class="Symbol">(</a><a id="21829" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="21833" href="plfa.part1.Relations.html#21811" class="Bound">n≤m</a><a id="21836" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
This is also our first use of a `where` clause in Agda.  The keyword `where` is
followed by one or more definitions, which must be indented.  Any variables
bound on the left-hand side of the preceding equation (in this case, `m` and
`n`) are in scope within the nested definition, and any identifiers bound in the
nested definition (in this case, `helper`) are in scope in the right-hand side
of the preceding equation.
{:/}

这也是我们第一次在 Agda 中使用 `where` 语句。`where` 关键字后面有一或多条定义，其必须被缩进。之前等式左手边的约束变量（此例中的 `m` 和 `n`）在嵌套的定义中仍然在作用域内。在嵌套定义中的约束标识符（此例中的 `helper` ）在等式的右手边的作用域内。

{::comment}
If both arguments are equal, then both cases hold and we could return evidence
of either.  In the code above we return the forward case, but there is a
variant that returns the flipped case:
{:/}

如果两个参数相同，那么两个情况同时成立，我们可以返回任一证明。上面的代码中我们返回 forward 条件，但是我们也可以返回 flipped 条件，如下：

{% raw %}<pre class="Agda"><a id="≤-total″"></a><a id="22720" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#22720" class="Function">≤-total″</a> <a id="22729" class="Symbol">:</a> <a id="22731" class="Symbol">∀</a> <a id="22733" class="Symbol">(</a><a id="22734" href="plfa.part1.Relations.html#22734" class="Bound">m</a> <a id="22736" href="plfa.part1.Relations.html#22736" class="Bound">n</a> <a id="22738" class="Symbol">:</a> <a id="22740" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="22741" class="Symbol">)</a> <a id="22743" class="Symbol">→</a> <a id="22745" href="plfa.part1.Relations.html#17146" class="Datatype">Total</a> <a id="22751" href="plfa.part1.Relations.html#22734" class="Bound">m</a> <a id="22753" href="plfa.part1.Relations.html#22736" class="Bound">n</a>
<a id="22755" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#22720" class="Function">≤-total″</a> <a id="22764" href="plfa.part1.Relations.html#22764" class="Bound">m</a>       <a id="22772" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>                      <a id="22798" class="Symbol">=</a>  <a id="22801" href="plfa.part1.Relations.html#17234" class="InductiveConstructor">flipped</a> <a id="22809" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>
<a id="22813" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#22720" class="Function">≤-total″</a> <a id="22822" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>    <a id="22830" class="Symbol">(</a><a id="22831" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="22835" href="plfa.part1.Relations.html#22835" class="Bound">n</a><a id="22836" class="Symbol">)</a>                   <a id="22856" class="Symbol">=</a>  <a id="22859" href="plfa.part1.Relations.html#17177" class="InductiveConstructor">forward</a> <a id="22867" href="plfa.part1.Relations.html#1494" class="InductiveConstructor">z≤n</a>
<a id="22871" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#22720" class="Function">≤-total″</a> <a id="22880" class="Symbol">(</a><a id="22881" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="22885" href="plfa.part1.Relations.html#22885" class="Bound">m</a><a id="22886" class="Symbol">)</a> <a id="22888" class="Symbol">(</a><a id="22889" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="22893" href="plfa.part1.Relations.html#22893" class="Bound">n</a><a id="22894" class="Symbol">)</a> <a id="22896" class="Keyword">with</a> <a id="22901" href="plfa.part1.Relations.html#22720" class="Function">≤-total″</a> <a id="22910" href="plfa.part1.Relations.html#22885" class="Bound">m</a> <a id="22912" href="plfa.part1.Relations.html#22893" class="Bound">n</a>
<a id="22914" class="Symbol">...</a>                        <a id="22941" class="Symbol">|</a> <a id="22943" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17177" class="InductiveConstructor">forward</a> <a id="22951" href="plfa.part1.Relations.html#22951" class="Bound">m≤n</a>   <a id="22957" class="Symbol">=</a>  <a id="22960" href="plfa.part1.Relations.html#17177" class="InductiveConstructor">forward</a> <a id="22968" class="Symbol">(</a><a id="22969" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="22973" href="plfa.part1.Relations.html#22951" class="Bound">m≤n</a><a id="22976" class="Symbol">)</a>
<a id="22978" class="Symbol">...</a>                        <a id="23005" class="Symbol">|</a> <a id="23007" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#17234" class="InductiveConstructor">flipped</a> <a id="23015" href="plfa.part1.Relations.html#23015" class="Bound">n≤m</a>   <a id="23021" class="Symbol">=</a>  <a id="23024" href="plfa.part1.Relations.html#17234" class="InductiveConstructor">flipped</a> <a id="23032" class="Symbol">(</a><a id="23033" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="23037" href="plfa.part1.Relations.html#23015" class="Bound">n≤m</a><a id="23040" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
It differs from the original code in that it pattern
matches on the second argument before the first argument.
{:/}

两者的区别在于上述代码在对于第一个参数进行模式匹配之前先对于第二个参数先进行模式匹配。


{::comment}
## Monotonicity
{:/}

## 单调性

{::comment}
If one bumps into both an operator and an ordering at a party, one may ask if
the operator is _monotonic_ with regard to the ordering.  For example, addition
is monotonic with regard to inequality, meaning:
{:/}

如果在聚会中碰到了一个运算符和一个序，那么有人可能会问这个运算符对于这个序是不是
**单调的（Monotonic）**。比如说，加法对于小于等于是单调的，这意味着：

    ∀ {m n p q : ℕ} → m ≤ n → p ≤ q → m + p ≤ n + q

{::comment}
The proof is straightforward using the techniques we have learned, and is best
broken into three parts. First, we deal with the special case of showing
addition is monotonic on the right:
{:/}

这个证明可以用我们学会的方法，很直接的来完成。我们最好把它分成三个部分，首先我们证明加法对于小于等于在右手边是单调的：

{% raw %}<pre class="Agda"><a id="+-monoʳ-≤"></a><a id="23898" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#23898" class="Function">+-monoʳ-≤</a> <a id="23908" class="Symbol">:</a> <a id="23910" class="Symbol">∀</a> <a id="23912" class="Symbol">(</a><a id="23913" href="plfa.part1.Relations.html#23913" class="Bound">n</a> <a id="23915" href="plfa.part1.Relations.html#23915" class="Bound">p</a> <a id="23917" href="plfa.part1.Relations.html#23917" class="Bound">q</a> <a id="23919" class="Symbol">:</a> <a id="23921" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="23922" class="Symbol">)</a>
  <a id="23926" class="Symbol">→</a> <a id="23928" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#23915" class="Bound">p</a> <a id="23930" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="23932" href="plfa.part1.Relations.html#23917" class="Bound">q</a>
    <a id="23938" class="Comment">-------------</a>
  <a id="23954" class="Symbol">→</a> <a id="23956" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#23913" class="Bound">n</a> <a id="23958" href="Agda.Builtin.Nat.html#298" class="Primitive Operator">+</a> <a id="23960" href="plfa.part1.Relations.html#23915" class="Bound">p</a> <a id="23962" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="23964" href="plfa.part1.Relations.html#23913" class="Bound">n</a> <a id="23966" href="Agda.Builtin.Nat.html#298" class="Primitive Operator">+</a> <a id="23968" href="plfa.part1.Relations.html#23917" class="Bound">q</a>
<a id="23970" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#23898" class="Function">+-monoʳ-≤</a> <a id="23980" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>    <a id="23988" href="plfa.part1.Relations.html#23988" class="Bound">p</a> <a id="23990" href="plfa.part1.Relations.html#23990" class="Bound">q</a> <a id="23992" href="plfa.part1.Relations.html#23992" class="Bound">p≤q</a>  <a id="23997" class="Symbol">=</a>  <a id="24000" href="plfa.part1.Relations.html#23992" class="Bound">p≤q</a>
<a id="24004" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#23898" class="Function">+-monoʳ-≤</a> <a id="24014" class="Symbol">(</a><a id="24015" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="24019" href="plfa.part1.Relations.html#24019" class="Bound">n</a><a id="24020" class="Symbol">)</a> <a id="24022" href="plfa.part1.Relations.html#24022" class="Bound">p</a> <a id="24024" href="plfa.part1.Relations.html#24024" class="Bound">q</a> <a id="24026" href="plfa.part1.Relations.html#24026" class="Bound">p≤q</a>  <a id="24031" class="Symbol">=</a>  <a id="24034" href="plfa.part1.Relations.html#1543" class="InductiveConstructor">s≤s</a> <a id="24038" class="Symbol">(</a><a id="24039" href="plfa.part1.Relations.html#23898" class="Function">+-monoʳ-≤</a> <a id="24049" href="plfa.part1.Relations.html#24019" class="Bound">n</a> <a id="24051" href="plfa.part1.Relations.html#24022" class="Bound">p</a> <a id="24053" href="plfa.part1.Relations.html#24024" class="Bound">q</a> <a id="24055" href="plfa.part1.Relations.html#24026" class="Bound">p≤q</a><a id="24058" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
The proof is by induction on the first argument.

* _Base case_: The first argument is `zero` in which case
  `zero + p ≤ zero + q` simplifies to `p ≤ q`, the evidence
  for which is given by the argument `p≤q`.

* _Inductive case_: The first argument is `suc n`, in which case
  `suc n + p ≤ suc n + q` simplifies to `suc (n + p) ≤ suc (n + q)`.
  The inductive hypothesis `+-monoʳ-≤ n p q p≤q` establishes that
  `n + p ≤ n + q`, and our goal follows by applying `s≤s`.
{:/}

我们对于第一个参数进行归纳。

* **起始步骤**：第一个参数是 `zero`，那么 `zero + p ≤ zero + q` 可以化简为 `p ≤ q`，
  其证明由 `p≤q` 给出。

* **归纳步骤**：第一个参数是 `suc n`，那么 `suc n + p ≤ suc n + q` 可以化简为
  `suc (n + p) ≤ suc (n + q)`。归纳假设 `+-monoʳ-≤ n p q p≤q` 可以证明
  `n + p ≤ n + q`，我们在此之上使用 `s≤s` 即可得证。

{::comment}
Second, we deal with the special case of showing addition is
monotonic on the left. This follows from the previous
result and the commutativity of addition:
{:/}

接下来，我们证明加法对于小于等于在左手边是单调的。我们可以用之前的结论和加法的交换律来证明：

{% raw %}<pre class="Agda"><a id="+-monoˡ-≤"></a><a id="25042" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#25042" class="Function">+-monoˡ-≤</a> <a id="25052" class="Symbol">:</a> <a id="25054" class="Symbol">∀</a> <a id="25056" class="Symbol">(</a><a id="25057" href="plfa.part1.Relations.html#25057" class="Bound">m</a> <a id="25059" href="plfa.part1.Relations.html#25059" class="Bound">n</a> <a id="25061" href="plfa.part1.Relations.html#25061" class="Bound">p</a> <a id="25063" class="Symbol">:</a> <a id="25065" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="25066" class="Symbol">)</a>
  <a id="25070" class="Symbol">→</a> <a id="25072" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#25057" class="Bound">m</a> <a id="25074" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="25076" href="plfa.part1.Relations.html#25059" class="Bound">n</a>
    <a id="25082" class="Comment">-------------</a>
  <a id="25098" class="Symbol">→</a> <a id="25100" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#25057" class="Bound">m</a> <a id="25102" href="Agda.Builtin.Nat.html#298" class="Primitive Operator">+</a> <a id="25104" href="plfa.part1.Relations.html#25061" class="Bound">p</a> <a id="25106" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="25108" href="plfa.part1.Relations.html#25059" class="Bound">n</a> <a id="25110" href="Agda.Builtin.Nat.html#298" class="Primitive Operator">+</a> <a id="25112" href="plfa.part1.Relations.html#25061" class="Bound">p</a>
<a id="25114" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#25042" class="Function">+-monoˡ-≤</a> <a id="25124" href="plfa.part1.Relations.html#25124" class="Bound">m</a> <a id="25126" href="plfa.part1.Relations.html#25126" class="Bound">n</a> <a id="25128" href="plfa.part1.Relations.html#25128" class="Bound">p</a> <a id="25130" href="plfa.part1.Relations.html#25130" class="Bound">m≤n</a>  <a id="25135" class="Keyword">rewrite</a> <a id="25143" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html#11911" class="Function">+-comm</a> <a id="25150" href="plfa.part1.Relations.html#25124" class="Bound">m</a> <a id="25152" href="plfa.part1.Relations.html#25128" class="Bound">p</a> <a id="25154" class="Symbol">|</a> <a id="25156" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html#11911" class="Function">+-comm</a> <a id="25163" href="plfa.part1.Relations.html#25126" class="Bound">n</a> <a id="25165" href="plfa.part1.Relations.html#25128" class="Bound">p</a>  <a id="25168" class="Symbol">=</a> <a id="25170" href="plfa.part1.Relations.html#23898" class="Function">+-monoʳ-≤</a> <a id="25180" href="plfa.part1.Relations.html#25128" class="Bound">p</a> <a id="25182" href="plfa.part1.Relations.html#25124" class="Bound">m</a> <a id="25184" href="plfa.part1.Relations.html#25126" class="Bound">n</a> <a id="25186" href="plfa.part1.Relations.html#25130" class="Bound">m≤n</a>
</pre>{% endraw %}
{::comment}
Rewriting by `+-comm m p` and `+-comm n p` converts `m + p ≤ n + p` into
`p + m ≤ p + n`, which is proved by invoking `+-monoʳ-≤ p m n m≤n`.
{:/}

用 `+-comm m p` 和 `+-comm n p` 来重写，可以让 `m + p ≤ n + p` 转换成 `p + n ≤ p + m`，而我们可以用 `+-moroʳ-≤ p m n m≤n` 来证明。

{::comment}
Third, we combine the two previous results:
{:/}

最后，我们把前两步的结论结合起来：

{% raw %}<pre class="Agda"><a id="+-mono-≤"></a><a id="25549" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#25549" class="Function">+-mono-≤</a> <a id="25558" class="Symbol">:</a> <a id="25560" class="Symbol">∀</a> <a id="25562" class="Symbol">(</a><a id="25563" href="plfa.part1.Relations.html#25563" class="Bound">m</a> <a id="25565" href="plfa.part1.Relations.html#25565" class="Bound">n</a> <a id="25567" href="plfa.part1.Relations.html#25567" class="Bound">p</a> <a id="25569" href="plfa.part1.Relations.html#25569" class="Bound">q</a> <a id="25571" class="Symbol">:</a> <a id="25573" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="25574" class="Symbol">)</a>
  <a id="25578" class="Symbol">→</a> <a id="25580" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#25563" class="Bound">m</a> <a id="25582" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="25584" href="plfa.part1.Relations.html#25565" class="Bound">n</a>
  <a id="25588" class="Symbol">→</a> <a id="25590" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#25567" class="Bound">p</a> <a id="25592" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="25594" href="plfa.part1.Relations.html#25569" class="Bound">q</a>
    <a id="25600" class="Comment">-------------</a>
  <a id="25616" class="Symbol">→</a> <a id="25618" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#25563" class="Bound">m</a> <a id="25620" href="Agda.Builtin.Nat.html#298" class="Primitive Operator">+</a> <a id="25622" href="plfa.part1.Relations.html#25567" class="Bound">p</a> <a id="25624" href="plfa.part1.Relations.html#1467" class="Datatype Operator">≤</a> <a id="25626" href="plfa.part1.Relations.html#25565" class="Bound">n</a> <a id="25628" href="Agda.Builtin.Nat.html#298" class="Primitive Operator">+</a> <a id="25630" href="plfa.part1.Relations.html#25569" class="Bound">q</a>
<a id="25632" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#25549" class="Function">+-mono-≤</a> <a id="25641" href="plfa.part1.Relations.html#25641" class="Bound">m</a> <a id="25643" href="plfa.part1.Relations.html#25643" class="Bound">n</a> <a id="25645" href="plfa.part1.Relations.html#25645" class="Bound">p</a> <a id="25647" href="plfa.part1.Relations.html#25647" class="Bound">q</a> <a id="25649" href="plfa.part1.Relations.html#25649" class="Bound">m≤n</a> <a id="25653" href="plfa.part1.Relations.html#25653" class="Bound">p≤q</a>  <a id="25658" class="Symbol">=</a>  <a id="25661" href="plfa.part1.Relations.html#12221" class="Function">≤-trans</a> <a id="25669" class="Symbol">(</a><a id="25670" href="plfa.part1.Relations.html#25042" class="Function">+-monoˡ-≤</a> <a id="25680" href="plfa.part1.Relations.html#25641" class="Bound">m</a> <a id="25682" href="plfa.part1.Relations.html#25643" class="Bound">n</a> <a id="25684" href="plfa.part1.Relations.html#25645" class="Bound">p</a> <a id="25686" href="plfa.part1.Relations.html#25649" class="Bound">m≤n</a><a id="25689" class="Symbol">)</a> <a id="25691" class="Symbol">(</a><a id="25692" href="plfa.part1.Relations.html#23898" class="Function">+-monoʳ-≤</a> <a id="25702" href="plfa.part1.Relations.html#25643" class="Bound">n</a> <a id="25704" href="plfa.part1.Relations.html#25645" class="Bound">p</a> <a id="25706" href="plfa.part1.Relations.html#25647" class="Bound">q</a> <a id="25708" href="plfa.part1.Relations.html#25653" class="Bound">p≤q</a><a id="25711" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
Invoking `+-monoˡ-≤ m n p m≤n` proves `m + p ≤ n + p` and invoking
`+-monoʳ-≤ n p q p≤q` proves `n + p ≤ n + q`, and combining these with
transitivity proves `m + p ≤ n + q`, as was to be shown.
{:/}

使用 `+-monoˡ-≤ m n p m≤n` 可以证明 `m + p ≤ n + p`，使用 `+-monoʳ-≤ n p q p≤q` 可以证明 `n + p ≤ n + q`，用传递性把两者连接起来，我们可以获得 `m + p ≤ n + q` 的证明，如上所示。

{::comment}
#### Exercise `*-mono-≤` (stretch)
{:/}

#### 练习 `*-mono-≤` （延伸）

{::comment}
Show that multiplication is monotonic with regard to inequality.
{:/}

证明乘法对于小于等于是单调的。

{::comment}
{% raw %}<pre class="Agda"><a id="26265" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="26302" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}

{::comment}
## Strict inequality {#strict-inequality}
{:/}

## 严格不等关系 {#strict-inequality}

{::comment}
We can define strict inequality similarly to inequality:
{:/}

我们可以用类似于定义不等关系的方法来定义严格不等关系。

{% raw %}<pre class="Agda"><a id="26521" class="Keyword">infix</a> <a id="26527" class="Number">4</a> <a id="26529" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#26539" class="Datatype Operator">_&lt;_</a>

<a id="26534" class="Keyword">data</a> <a id="_&lt;_"></a><a id="26539" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#26539" class="Datatype Operator">_&lt;_</a> <a id="26543" class="Symbol">:</a> <a id="26545" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a> <a id="26547" class="Symbol">→</a> <a id="26549" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a> <a id="26551" class="Symbol">→</a> <a id="26553" class="PrimitiveType">Set</a> <a id="26557" class="Keyword">where</a>

  <a id="_&lt;_.z&lt;s"></a><a id="26566" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#26566" class="InductiveConstructor">z&lt;s</a> <a id="26570" class="Symbol">:</a> <a id="26572" class="Symbol">∀</a> <a id="26574" class="Symbol">{</a><a id="26575" href="plfa.part1.Relations.html#26575" class="Bound">n</a> <a id="26577" class="Symbol">:</a> <a id="26579" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="26580" class="Symbol">}</a>
      <a id="26588" class="Comment">------------</a>
    <a id="26605" class="Symbol">→</a> <a id="26607" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a> <a id="26612" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#26539" class="Datatype Operator">&lt;</a> <a id="26614" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="26618" href="plfa.part1.Relations.html#26575" class="Bound">n</a>

  <a id="_&lt;_.s&lt;s"></a><a id="26623" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#26623" class="InductiveConstructor">s&lt;s</a> <a id="26627" class="Symbol">:</a> <a id="26629" class="Symbol">∀</a> <a id="26631" class="Symbol">{</a><a id="26632" href="plfa.part1.Relations.html#26632" class="Bound">m</a> <a id="26634" href="plfa.part1.Relations.html#26634" class="Bound">n</a> <a id="26636" class="Symbol">:</a> <a id="26638" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="26639" class="Symbol">}</a>
    <a id="26645" class="Symbol">→</a> <a id="26647" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#26632" class="Bound">m</a> <a id="26649" href="plfa.part1.Relations.html#26539" class="Datatype Operator">&lt;</a> <a id="26651" href="plfa.part1.Relations.html#26634" class="Bound">n</a>
      <a id="26659" class="Comment">-------------</a>
    <a id="26677" class="Symbol">→</a> <a id="26679" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="26683" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#26632" class="Bound">m</a> <a id="26685" href="plfa.part1.Relations.html#26539" class="Datatype Operator">&lt;</a> <a id="26687" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="26691" href="plfa.part1.Relations.html#26634" class="Bound">n</a>
</pre>{% endraw %}
{::comment}
The key difference is that zero is less than the successor of an
arbitrary number, but is not less than zero.
{:/}

严格不等关系与不等关系最重要的区别在于，0 小于任何数的后继，而不小于 0。

{::comment}
Clearly, strict inequality is not reflexive. However it is
_irreflexive_ in that `n < n` never holds for any value of `n`.
Like inequality, strict inequality is transitive.
Strict inequality is not total, but satisfies the closely related property of
_trichotomy_: for any `m` and `n`, exactly one of `m < n`, `m ≡ n`, or `m > n`
holds (where we define `m > n` to hold exactly when `n < m`).
It is also monotonic with regards to addition and multiplication.
{:/}

显然，严格不等关系不是自反的，而是**非自反的（Irreflexive）**，表示 `n < n` 对于任何值 `n` 都不成立。和不等关系一样，严格不等关系是传递的。严格不等关系不是完全的，但是满足一个相似的性质：*三分律*（Trichotomy）：对于任意的 `m` 和 `n`，`m < n`、`m ≡ n` 或者
`m > n` 三者有且仅有一者成立。（我们定义 `m > n` 当且仅当 `n < m` 成立时成立）
严格不等关系对于加法和乘法也是单调的。

{::comment}
Most of the above are considered in exercises below.  Irreflexivity
requires negation, as does the fact that the three cases in
trichotomy are mutually exclusive, so those points are deferred to
Chapter [Negation]({{ site.baseurl }}/Negation/).
{:/}

我们把一部分上述性质作为习题。非自反性需要逻辑非，三分律需要证明三者是互斥的，因此这两个性质暂不做为习题。我们会在 [Negation]({{ site.baseurl }}/Negation/) 章节来重新讨论。

{::comment}
It is straightforward to show that `suc m ≤ n` implies `m < n`,
and conversely.  One can then give an alternative derivation of the
properties of strict inequality, such as transitivity, by
exploiting the corresponding properties of inequality.
{:/}

我们可以直接地来证明 `suc m ≤ n` 蕴涵了 `m < n`，及其逆命题。因此我们亦可从不等关系的性质中，使用此性质来证明严格不等关系的性质。


{::comment}
#### Exercise `<-trans` (recommended) {#less-trans}
{:/}

#### 练习 `<-trans` （推荐） {#less-trans}

{::comment}
Show that strict inequality is transitive.
{:/}

证明严格不等是传递的。

{::comment}
{% raw %}<pre class="Agda"><a id="28492" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="28529" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}

{::comment}
#### Exercise `trichotomy` (practice) {#trichotomy}
{:/}

#### 练习 `trichotomy`（实践） {#trichotomy}

{::comment}
Show that strict inequality satisfies a weak version of trichotomy, in
the sense that for any `m` and `n` that one of the following holds:
  * `m < n`,
  * `m ≡ n`, or
  * `m > n`.
{:/}

证明严格不等关系满足弱化的三元律，证明对于任意 `m` 和 `n`，下列命题有一条成立：

  * `m < n`，
  * `m ≡ n`，或者
  * `m > n`。

{::comment}
Define `m > n` to be the same as `n < m`.
You will need a suitable data declaration,
similar to that used for totality.
(We will show that the three cases are exclusive after we introduce
[negation]({{ site.baseurl }}/Negation/).)
{:/}

定义 `m > n` 为 `n < m`。你需要一个合适的数据类型声明，如同我们在证明完全性中使用的那样。
（我们会在介绍完[否定]({{ site.baseurl }}/Negation/)之后证明三者是互斥的。）

{::comment}
{% raw %}<pre class="Agda"><a id="29320" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="29357" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}
{::comment}
#### Exercise `+-mono-<` (practice) {#plus-mono-less}
{:/}

#### 练习 `+-mono-<`（实践） {#plus-mono-less}

{::comment}
Show that addition is monotonic with respect to strict inequality.
As with inequality, some additional definitions may be required.
{:/}

证明加法对于严格不等关系是单调的。正如不等关系中那样，你可以需要额外的定义。

{::comment}
{% raw %}<pre class="Agda"><a id="29695" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="29732" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}

{::comment}
#### Exercise `≤-iff-<` (recommended) {#leq-iff-less}
{:/}

#### 练习 `≤-iff-<` (推荐) {#leq-iff-less}

{::comment}
Show that `suc m ≤ n` implies `m < n`, and conversely.
{:/}

证明 `suc m ≤ n` 蕴涵了 `m < n`，及其逆命题。

{::comment}
{% raw %}<pre class="Agda"><a id="29987" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="30024" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}
{::comment}
#### Exercise `<-trans-revisited` (practice) {#less-trans-revisited}
{:/}

#### 练习 `<-trans-revisited`（实践） {#less-trans-revisited}

{::comment}
Give an alternative proof that strict inequality is transitive,
using the relation between strict inequality and inequality and
the fact that inequality is transitive.
{:/}

用另外一种方法证明严格不等是传递的，使用之前证明的不等关系和严格不等关系的联系，以及不等关系的传递性。

{::comment}
{% raw %}<pre class="Agda"><a id="30442" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="30479" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}

{::comment}
## Even and odd
{:/}

## 奇和偶

{::comment}
As a further example, let's specify even and odd numbers.  Inequality
and strict inequality are _binary relations_, while even and odd are
_unary relations_, sometimes called _predicates_:
{:/}

作为一个额外的例子，我们来定义奇数和偶数。不等关系和严格不等关系是**二元关系**，而奇偶性是**一元关系**，有时也被叫做**谓词（Predicate）**：

{% raw %}<pre class="Agda"><a id="30834" class="Keyword">data</a> <a id="even"></a><a id="30839" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30839" class="Datatype">even</a> <a id="30844" class="Symbol">:</a> <a id="30846" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a> <a id="30848" class="Symbol">→</a> <a id="30850" class="PrimitiveType">Set</a>
<a id="30854" class="Keyword">data</a> <a id="odd"></a><a id="30859" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30859" class="Datatype">odd</a>  <a id="30864" class="Symbol">:</a> <a id="30866" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a> <a id="30868" class="Symbol">→</a> <a id="30870" class="PrimitiveType">Set</a>

<a id="30875" class="Keyword">data</a> <a id="30880" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30839" class="Datatype">even</a> <a id="30885" class="Keyword">where</a>

  <a id="even.zero"></a><a id="30894" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30894" class="InductiveConstructor">zero</a> <a id="30899" class="Symbol">:</a>
      <a id="30907" class="Comment">---------</a>
      <a id="30923" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30839" class="Datatype">even</a> <a id="30928" href="Agda.Builtin.Nat.html#183" class="InductiveConstructor">zero</a>

  <a id="even.suc"></a><a id="30936" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30936" class="InductiveConstructor">suc</a>  <a id="30941" class="Symbol">:</a> <a id="30943" class="Symbol">∀</a> <a id="30945" class="Symbol">{</a><a id="30946" href="plfa.part1.Relations.html#30946" class="Bound">n</a> <a id="30948" class="Symbol">:</a> <a id="30950" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="30951" class="Symbol">}</a>
    <a id="30957" class="Symbol">→</a> <a id="30959" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30859" class="Datatype">odd</a> <a id="30963" href="plfa.part1.Relations.html#30946" class="Bound">n</a>
      <a id="30971" class="Comment">------------</a>
    <a id="30988" class="Symbol">→</a> <a id="30990" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30839" class="Datatype">even</a> <a id="30995" class="Symbol">(</a><a id="30996" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="31000" href="plfa.part1.Relations.html#30946" class="Bound">n</a><a id="31001" class="Symbol">)</a>

<a id="31004" class="Keyword">data</a> <a id="31009" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30859" class="Datatype">odd</a> <a id="31013" class="Keyword">where</a>

  <a id="odd.suc"></a><a id="31022" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#31022" class="InductiveConstructor">suc</a>   <a id="31028" class="Symbol">:</a> <a id="31030" class="Symbol">∀</a> <a id="31032" class="Symbol">{</a><a id="31033" href="plfa.part1.Relations.html#31033" class="Bound">n</a> <a id="31035" class="Symbol">:</a> <a id="31037" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="31038" class="Symbol">}</a>
    <a id="31044" class="Symbol">→</a> <a id="31046" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30839" class="Datatype">even</a> <a id="31051" href="plfa.part1.Relations.html#31033" class="Bound">n</a>
      <a id="31059" class="Comment">-----------</a>
    <a id="31075" class="Symbol">→</a> <a id="31077" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30859" class="Datatype">odd</a> <a id="31081" class="Symbol">(</a><a id="31082" href="Agda.Builtin.Nat.html#196" class="InductiveConstructor">suc</a> <a id="31086" href="plfa.part1.Relations.html#31033" class="Bound">n</a><a id="31087" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
A number is even if it is zero or the successor of an odd number,
and odd if it is the successor of an even number.
{:/}

一个数是偶数，如果它是 0，或者是奇数的后继。一个数是奇数，如果它是偶数的后继。

{::comment}
This is our first use of a mutually recursive datatype declaration.
Since each identifier must be defined before it is used, we first
declare the indexed types `even` and `odd` (omitting the `where`
keyword and the declarations of the constructors) and then
declare the constructors (omitting the signatures `ℕ → Set`
which were given earlier).
{:/}

这是我们第一次定义一个相互递归的数据类型。因为每个标识符必须在使用前声明，所以我们首先声明索引数据类型 `even` 和 `odd` （省略 `where` 关键字和其构造子的定义），然后声明其构造子（省略其签名 `ℕ → Set`，因为在之前已经给出）。

{::comment}
This is also our first use of _overloaded_ constructors,
that is, using the same name for constructors of different types.
Here `suc` means one of three constructors:
{:/}

这也是我们第一次使用 **重载（Overloaded）**的构造子。这意味着不同类型的构造子拥有相同的名字。在这里 `suc` 表示下面三种构造子其中之一：

    suc : ℕ → ℕ

    suc : ∀ {n : ℕ}
      → odd n
        ------------
      → even (suc n)

    suc : ∀ {n : ℕ}
      → even n
        -----------
      → odd (suc n)

{::comment}
Similarly, `zero` refers to one of two constructors. Due to how it
does type inference, Agda does not allow overloading of defined names,
but does allow overloading of constructors.  It is recommended that
one restrict overloading to related meanings, as we have done here,
but it is not required.
{:/}

同理，`zero` 表示两种构造子的一种。因为类型推导的限制，Agda 不允许重载已定义的名字，但是允许重载构造子。我们推荐将重载限制在有关联的定义中，如我们所做的这样，但这不是必须的。

{::comment}
We show that the sum of two even numbers is even:
{:/}

我们证明两个偶数之和是偶数：

{% raw %}<pre class="Agda"><a id="e+e≡e"></a><a id="32701" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#32701" class="Function">e+e≡e</a> <a id="32707" class="Symbol">:</a> <a id="32709" class="Symbol">∀</a> <a id="32711" class="Symbol">{</a><a id="32712" href="plfa.part1.Relations.html#32712" class="Bound">m</a> <a id="32714" href="plfa.part1.Relations.html#32714" class="Bound">n</a> <a id="32716" class="Symbol">:</a> <a id="32718" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="32719" class="Symbol">}</a>
  <a id="32723" class="Symbol">→</a> <a id="32725" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30839" class="Datatype">even</a> <a id="32730" href="plfa.part1.Relations.html#32712" class="Bound">m</a>
  <a id="32734" class="Symbol">→</a> <a id="32736" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30839" class="Datatype">even</a> <a id="32741" href="plfa.part1.Relations.html#32714" class="Bound">n</a>
    <a id="32747" class="Comment">------------</a>
  <a id="32762" class="Symbol">→</a> <a id="32764" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30839" class="Datatype">even</a> <a id="32769" class="Symbol">(</a><a id="32770" href="plfa.part1.Relations.html#32712" class="Bound">m</a> <a id="32772" href="Agda.Builtin.Nat.html#298" class="Primitive Operator">+</a> <a id="32774" href="plfa.part1.Relations.html#32714" class="Bound">n</a><a id="32775" class="Symbol">)</a>

<a id="o+e≡o"></a><a id="32778" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#32778" class="Function">o+e≡o</a> <a id="32784" class="Symbol">:</a> <a id="32786" class="Symbol">∀</a> <a id="32788" class="Symbol">{</a><a id="32789" href="plfa.part1.Relations.html#32789" class="Bound">m</a> <a id="32791" href="plfa.part1.Relations.html#32791" class="Bound">n</a> <a id="32793" class="Symbol">:</a> <a id="32795" href="Agda.Builtin.Nat.html#165" class="Datatype">ℕ</a><a id="32796" class="Symbol">}</a>
  <a id="32800" class="Symbol">→</a> <a id="32802" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30859" class="Datatype">odd</a> <a id="32806" href="plfa.part1.Relations.html#32789" class="Bound">m</a>
  <a id="32810" class="Symbol">→</a> <a id="32812" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30839" class="Datatype">even</a> <a id="32817" href="plfa.part1.Relations.html#32791" class="Bound">n</a>
    <a id="32823" class="Comment">-----------</a>
  <a id="32837" class="Symbol">→</a> <a id="32839" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#30859" class="Datatype">odd</a> <a id="32843" class="Symbol">(</a><a id="32844" href="plfa.part1.Relations.html#32789" class="Bound">m</a> <a id="32846" href="Agda.Builtin.Nat.html#298" class="Primitive Operator">+</a> <a id="32848" href="plfa.part1.Relations.html#32791" class="Bound">n</a><a id="32849" class="Symbol">)</a>

<a id="32852" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#32701" class="Function">e+e≡e</a> <a id="32858" href="plfa.part1.Relations.html#30894" class="InductiveConstructor">zero</a>     <a id="32867" href="plfa.part1.Relations.html#32867" class="Bound">en</a>  <a id="32871" class="Symbol">=</a>  <a id="32874" href="plfa.part1.Relations.html#32867" class="Bound">en</a>
<a id="32877" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#32701" class="Function">e+e≡e</a> <a id="32883" class="Symbol">(</a><a id="32884" href="plfa.part1.Relations.html#30936" class="InductiveConstructor">suc</a> <a id="32888" href="plfa.part1.Relations.html#32888" class="Bound">om</a><a id="32890" class="Symbol">)</a> <a id="32892" href="plfa.part1.Relations.html#32892" class="Bound">en</a>  <a id="32896" class="Symbol">=</a>  <a id="32899" href="plfa.part1.Relations.html#30936" class="InductiveConstructor">suc</a> <a id="32903" class="Symbol">(</a><a id="32904" href="plfa.part1.Relations.html#32778" class="Function">o+e≡o</a> <a id="32910" href="plfa.part1.Relations.html#32888" class="Bound">om</a> <a id="32913" href="plfa.part1.Relations.html#32892" class="Bound">en</a><a id="32915" class="Symbol">)</a>

<a id="32918" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/part1/Relations.md %}{% raw %}#32778" class="Function">o+e≡o</a> <a id="32924" class="Symbol">(</a><a id="32925" href="plfa.part1.Relations.html#31022" class="InductiveConstructor">suc</a> <a id="32929" href="plfa.part1.Relations.html#32929" class="Bound">em</a><a id="32931" class="Symbol">)</a> <a id="32933" href="plfa.part1.Relations.html#32933" class="Bound">en</a>  <a id="32937" class="Symbol">=</a>  <a id="32940" href="plfa.part1.Relations.html#31022" class="InductiveConstructor">suc</a> <a id="32944" class="Symbol">(</a><a id="32945" href="plfa.part1.Relations.html#32701" class="Function">e+e≡e</a> <a id="32951" href="plfa.part1.Relations.html#32929" class="Bound">em</a> <a id="32954" href="plfa.part1.Relations.html#32933" class="Bound">en</a><a id="32956" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
Corresponding to the mutually recursive types, we use two mutually recursive
functions, one to show that the sum of two even numbers is even, and the other
to show that the sum of an odd and an even number is odd.
{:/}

与相互递归的定义对应，我们用两个相互递归的函数，一个证明两个偶数之和是偶数，另一个证明一个奇数与一个偶数之和是奇数。

{::comment}
This is our first use of mutually recursive functions.  Since each identifier
must be defined before it is used, we first give the signatures for both
functions and then the equations that define them.
{:/}

这是我们第一次使用相互递归的函数。因为每个标识符必须在使用前声明，我们先给出两个函数的签名，然后再给出其定义。

{::comment}
To show that the sum of two even numbers is even, consider the
evidence that the first number is even. If it is because it is zero,
then the sum is even because the second number is even.  If it is
because it is the successor of an odd number, then the result is even
because it is the successor of the sum of an odd and an even number,
which is odd.
{:/}

要证明两个偶数之和为偶，我们考虑第一个数为偶数的证明。如果是因为第一个数为 0，那么第二个数为偶数的证明即为和为偶数的证明。如果是因为第一个数为奇数的后继，那么和为偶数是因为他是一个奇数和一个偶数的和的后续，而这个和是一个奇数。


{::comment}
To show that the sum of an odd and even number is odd, consider the
evidence that the first number is odd. If it is because it is the
successor of an even number, then the result is odd because it is the
successor of the sum of two even numbers, which is even.
{:/}

要证明一个奇数和一个偶数的和是奇数，我们考虑第一个数是奇数的证明。如果是因为它是一个偶数的后继，那么和为奇数，因为它是两个偶数之和的后继，而这个和是一个偶数。


{::comment}
#### Exercise `o+o≡e` (stretch) {#odd-plus-odd}
{:/}

#### 练习 `o+o≡e` (延伸) {#odd-plus-odd}

{::comment}
Show that the sum of two odd numbers is even.
{:/}

证明两个奇数之和为偶数。

{::comment}
{% raw %}<pre class="Agda"><a id="34583" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="34620" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}

{::comment}
#### Exercise `Bin-predicates` (stretch) {#Bin-predicates}
{:/}

#### 练习 `Bin-predicates` (延伸) {#Bin-predicates}

{::comment}
Recall that
Exercise [Bin]({{ site.baseurl }}/Naturals/#Bin)
defines a datatype `Bin` of bitstrings representing natural numbers.
Representations are not unique due to leading zeros.
Hence, eleven may be represented by both of the following:
{:/}

回忆我们在练习 [Bin][plfa.Naturals#Bin] 中定义了一个数据类型 `Bin` 来用二进制字符串表示自然数。这个表达方法不是唯一的，因为我们在开头加任意个 0。因此，11 可以由以下方法表示：

    ⟨⟩ I O I I
    ⟨⟩ O O I O I I

{::comment}
Define a predicate
{:/}

定义一个谓词

    Can : Bin → Set

{::comment}
over all bitstrings that holds if the bitstring is canonical, meaning
it has no leading zeros; the first representation of eleven above is
canonical, and the second is not.  To define it, you will need an
auxiliary predicate
{:/}

其在一个二进制字符串的表示是标准的（Canonical）时成立，表示它没有开头的 0。在两个 11 的表达方式中，第一个是标准的，而第二个不是。在定义这个谓词时，你需要一个辅助谓词：

    One : Bin → Set

{::comment}
that holds only if the bistring has a leading one.  A bitstring is
canonical if it has a leading one (representing a positive number) or
if it consists of a single zero (representing zero).
{:/}

其仅在一个二进制字符串开头为 1 时成立。一个二进制字符串是标准的，如果它开头是 1 （表示一个正数），或者它仅是一个 0 （表示 0）。

{::comment}
Show that increment preserves canonical bitstrings:
{:/}

证明递增可以保持标准性。

    Can b
    ------------
    Can (inc b)

{::comment}
Show that converting a natural to a bitstring always yields a
canonical bitstring:
{:/}

证明从自然数转换成的二进制字符串是标准的。

    ----------
    Can (to n)

{::comment}
Show that converting a canonical bitstring to a natural
and back is the identity:
{:/}

证明将一个标准的二进制字符串转换成自然数之后，再转换回二进制字符串与原二进制字符串相同。

    Can b
    ---------------
    to (from b) ≡ b

{::comment}
(Hint: For each of these, you may first need to prove related
properties of `One`.)
{:/}

（提示：对于每一条习题，先从 `One` 的性质开始）

{::comment}
{% raw %}<pre class="Agda"><a id="36500" class="Comment">-- Your code goes here</a>
</pre>{% endraw %}{:/}

{% raw %}<pre class="Agda"><a id="36537" class="Comment">-- 请将代码写在此处。</a>
</pre>{% endraw %}

{::comment}
## Standard library
{:/}

## 标准库

{::comment}
Definitions similar to those in this chapter can be found in the standard library:
{:/}

标准库中有类似于本章介绍的定义：

{% raw %}<pre class="Agda"><a id="36725" class="Keyword">import</a> <a id="36732" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.html" class="Module">Data.Nat</a> <a id="36741" class="Keyword">using</a> <a id="36747" class="Symbol">(</a><a id="36748" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Base.html#895" class="Datatype Operator">_≤_</a><a id="36751" class="Symbol">;</a> <a id="36753" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Base.html#918" class="InductiveConstructor">z≤n</a><a id="36756" class="Symbol">;</a> <a id="36758" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Base.html#960" class="InductiveConstructor">s≤s</a><a id="36761" class="Symbol">)</a>
<a id="36763" class="Keyword">import</a> <a id="36770" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html" class="Module">Data.Nat.Properties</a> <a id="36790" class="Keyword">using</a> <a id="36796" class="Symbol">(</a><a id="36797" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html#3632" class="Function">≤-refl</a><a id="36803" class="Symbol">;</a> <a id="36805" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html#3815" class="Function">≤-trans</a><a id="36812" class="Symbol">;</a> <a id="36814" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html#3682" class="Function">≤-antisym</a><a id="36823" class="Symbol">;</a> <a id="36825" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html#3927" class="Function">≤-total</a><a id="36832" class="Symbol">;</a>
                                  <a id="36868" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html#15619" class="Function">+-monoʳ-≤</a><a id="36877" class="Symbol">;</a> <a id="36879" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html#15529" class="Function">+-monoˡ-≤</a><a id="36888" class="Symbol">;</a> <a id="36890" href="https://agda.github.io/agda-stdlib/v1.1/Data.Nat.Properties.html#15373" class="Function">+-mono-≤</a><a id="36898" class="Symbol">)</a>
</pre>{% endraw %}
{::comment}
In the standard library, `≤-total` is formalised in terms of
disjunction (which we define in
Chapter [Connectives]({{ site.baseurl }}/Connectives/)),
and `+-monoʳ-≤`, `+-monoˡ-≤`, `+-mono-≤` are proved differently than here,
and more arguments are implicit.
{:/}

在标准库中，`≤-total` 是使用析取定义的（我们将在 [Connectives][plfa.Connectives] 章节定义）。
`+-monoʳ-≤`、`+-monoˡ-≤` 和 `+-mono-≤` 的证明方法和本书不同。更多的参数是隐式申明的。


## Unicode

{::comment}
This chapter uses the following unicode:

    ≤  U+2264  LESS-THAN OR EQUAL TO (\<=, \le)
    ≥  U+2265  GREATER-THAN OR EQUAL TO (\>=, \ge)
    ˡ  U+02E1  MODIFIER LETTER SMALL L (\^l)
    ʳ  U+02B3  MODIFIER LETTER SMALL R (\^r)
{:/}

本章使用了如下 Unicode 符号：

    ≤  U+2264  小于等于 (\<=, \le)
    ≥  U+2265  大于等于 (\>=, \ge)
    ˡ  U+02E1  小写字母 L 标识符 (\^l)
    ʳ  U+02B3  小写字母 R 标识符 (\^r)

{::comment}
The commands `\^l` and `\^r` give access to a variety of superscript
leftward and rightward arrows in addition to superscript letters `l` and `r`.
{:/}

`\^l` 和 `\^r` 命令给出了左右箭头，以及上标字母 `l` 和 `r`。
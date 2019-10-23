---
title: '! (null 免除) 演算子 - C# リファレンス'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: cf941e5e3fa3fc6313ef8b2ff5c176aec68c1e6b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291681"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="4da2f-103">!</span><span class="sxs-lookup"><span data-stu-id="4da2f-103">!</span></span> <span data-ttu-id="4da2f-104">(null 免除) 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4da2f-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="4da2f-105">C# 8.0 以降では、単項の接尾辞 `!` 演算子は null 免除演算子です。</span><span class="sxs-lookup"><span data-stu-id="4da2f-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="4da2f-106">有効な [null 許容注釈コンテキスト](../../nullable-references.md#nullable-annotation-context)では、null 免除演算子を使用して、参照型の式 `x` が null ではないことを宣言します (`x!`)。</span><span class="sxs-lookup"><span data-stu-id="4da2f-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't null: `x!`.</span></span> <span data-ttu-id="4da2f-107">単項の接頭辞 `!` 演算子は、[論理否定演算子](boolean-logical-operators.md#logical-negation-operator-)です。</span><span class="sxs-lookup"><span data-stu-id="4da2f-107">The unary prefix `!` operator is a [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="4da2f-108">null 免除演算子は実行時には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="4da2f-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="4da2f-109">式の null 状態を変更することによって、コンパイラの静的フロー分析にのみ影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="4da2f-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="4da2f-110">実行時に、式 `x!` は基になる式 `x` の結果に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4da2f-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="4da2f-111">null 許容参照型の機能の詳細については、「[null 許容参照型](../../nullable-references.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4da2f-111">For more information about the nullable reference types feature, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="examples"></a><span data-ttu-id="4da2f-112">例</span><span class="sxs-lookup"><span data-stu-id="4da2f-112">Examples</span></span>

<span data-ttu-id="4da2f-113">null 免除演算子のユース ケースの 1 つは、引数検証ロジックをテストすることです。</span><span class="sxs-lookup"><span data-stu-id="4da2f-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="4da2f-114">たとえば、次のクラスを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="4da2f-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="4da2f-115">[MSTest テスト フレームワーク](../../../core/testing/unit-testing-with-mstest.md) を使用して、コンストラクターの検証ロジックに対して次のテストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4da2f-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="4da2f-116">null 免除演算子を使用しない場合は、コンパイラによって上のコードに対して次の警告が生成されます: `Warning CS8625: Cannot convert null literal to non-nullable reference type`。</span><span class="sxs-lookup"><span data-stu-id="4da2f-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="4da2f-117">null 免除演算子を使用すると、`null` を渡すことが予測されており、警告を生成しないことがコンパイラに通知されます。</span><span class="sxs-lookup"><span data-stu-id="4da2f-117">With the use of the null-forgiving operator, you let the compiler know that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="4da2f-118">また、式を `null` にできないことが明確にわかっているが、コンパイラでそのことを認識できない場合にも、null 免除演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4da2f-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="4da2f-119">次の例では、`IsValid` メソッドによって `true` が返された場合、その引数は `null` ではなく、安全に逆参照できます。</span><span class="sxs-lookup"><span data-stu-id="4da2f-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="4da2f-120">null 免除演算子を使用しない場合は、コンパイラによって `p.Name` コードに対して次の警告が生成されます: `Warning CS8602: Dereference of a possibly null reference.`。</span><span class="sxs-lookup"><span data-stu-id="4da2f-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference.`.</span></span>

<span data-ttu-id="4da2f-121">`IsValid` メソッドを変更できる場合は、[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) 属性を使用して、メソッドによって `true` が返されたときに `IsValid` メソッドの引数を `null` にできないことをコンパイラに通知することができます。</span><span class="sxs-lookup"><span data-stu-id="4da2f-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to let the compiler know that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="4da2f-122">前の例では、null 免除演算子を使用する必要はありません。これは、`if` ステートメント内で `p` を `null` にできないことを把握するのに十分な情報がコンパイラに含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="4da2f-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="4da2f-123">変数の null 状態に関する追加情報を指定するための属性の詳細については、[null 予測を定義する属性を使用した API のアップグレード](../../nullable-attributes.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4da2f-123">For more information about the attributes that allow you to specify additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4da2f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="4da2f-124">See also</span></span>

- [<span data-ttu-id="4da2f-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="4da2f-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4da2f-126">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="4da2f-126">C# operators</span></span>](index.md)
- [<span data-ttu-id="4da2f-127">チュートリアル:null 許容参照型を使用して設計する</span><span class="sxs-lookup"><span data-stu-id="4da2f-127">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
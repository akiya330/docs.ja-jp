---
title: '方法: ローカライズされた例外メッセージを使用するユーザー定義の例外を作成する'
description: ローカライズされた例外メッセージを使用するユーザー定義の例外を作成する方法について説明します。
author: Youssef1313
ms.author: ronpet
ms.date: 09/13/2019
ms.openlocfilehash: 1e5ef5658e4cb71d0689a1786494eaec57d4e7fb
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332963"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="d0738-103">方法: ローカライズされた例外メッセージを使用するユーザー定義の例外を作成する</span><span class="sxs-lookup"><span data-stu-id="d0738-103">How to: create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="d0738-104">この記事では、サテライト アセンブリを使用してローカライズされた例外メッセージ使用する、基底の <xref:System.Exception> クラスから継承されるユーザー定義の例外を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d0738-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="d0738-105">カスタムの例外を作成する</span><span class="sxs-lookup"><span data-stu-id="d0738-105">Create custom exceptions</span></span>

<span data-ttu-id="d0738-106">.NET には、使用できるさまざまな例外があります。</span><span class="sxs-lookup"><span data-stu-id="d0738-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="d0738-107">ただし、いずれもニーズに合わない場合は、独自のカスタムの例外を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d0738-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="d0738-108">たとえば、`StudentName` プロパティを含む `StudentNotFoundException` を作成するとします。</span><span class="sxs-lookup"><span data-stu-id="d0738-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="d0738-109">カスタムの例外を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d0738-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="d0738-110"><xref:System.Exception> から継承されるシリアル化可能なクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0738-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="d0738-111">クラス名の末尾は "Exception" にするようにします。</span><span class="sxs-lookup"><span data-stu-id="d0738-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

1. <span data-ttu-id="d0738-112">既定のコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="d0738-112">Add the default constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

1. <span data-ttu-id="d0738-113">追加のプロパティとコンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="d0738-113">Define any additional properties and constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

## <a name="create-localized-exception-messages"></a><span data-ttu-id="d0738-114">ローカライズされた例外メッセージを作成する</span><span class="sxs-lookup"><span data-stu-id="d0738-114">Create localized exception messages</span></span>

<span data-ttu-id="d0738-115">カスタムの例外を作成すると、次のようなコードを使用して任意の場所に例外をスローすることができます。</span><span class="sxs-lookup"><span data-stu-id="d0738-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

<span data-ttu-id="d0738-116">前の行の問題は、"The student cannot be found."</span><span class="sxs-lookup"><span data-stu-id="d0738-116">The problem with the previous line is that "The student cannot be found."</span></span> <span data-ttu-id="d0738-117">が単なる定数の文字列であることです。</span><span class="sxs-lookup"><span data-stu-id="d0738-117">is just a constant string.</span></span> <span data-ttu-id="d0738-118">ローカライズされるアプリケーションでは、ユーザーのカルチャに応じて異なるメッセージを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0738-118">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="d0738-119">[サテライト アセンブリ](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)はこの処理に適しています。</span><span class="sxs-lookup"><span data-stu-id="d0738-119">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="d0738-120">サテライト アセンブリは、特定の言語のリソースを含む .dll です。</span><span class="sxs-lookup"><span data-stu-id="d0738-120">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="d0738-121">実行時に特定のリソースを要求すると、ユーザーのカルチャに応じて CLR によってそのリソースが検索されます。</span><span class="sxs-lookup"><span data-stu-id="d0738-121">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="d0738-122">そのカルチャのサテライト アセンブリが見つからない場合は、既定のカルチャのリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d0738-122">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="d0738-123">ローカライズされた例外メッセージを作成するには:</span><span class="sxs-lookup"><span data-stu-id="d0738-123">To create the localized exception messages:</span></span>

1. <span data-ttu-id="d0738-124">リソース ファイルを保持するために、*Resources* という名前の新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0738-124">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="d0738-125">そこに新しいリソース ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="d0738-125">Add a new resource file to it.</span></span> <span data-ttu-id="d0738-126">Visual Studio でこれを行うには、**ソリューション エクスプローラー**でフォルダーを右クリックし、 **[追加]**  ->  **[新しい項目]**  ->  **[リソース ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0738-126">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** -> **New Item** -> **Resources File**.</span></span> <span data-ttu-id="d0738-127">ファイルに *ExceptionMessages.resx* という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="d0738-127">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="d0738-128">これは既定のリソース ファイルです。</span><span class="sxs-lookup"><span data-stu-id="d0738-128">This is the default resources file.</span></span>
1. <span data-ttu-id="d0738-129">次の図に示すように、例外メッセージの名前と値のペアを追加します。![既定のカルチャにリソースを追加する](media/add-resources-to-default-culture.jpg)</span><span class="sxs-lookup"><span data-stu-id="d0738-129">Add a name/value pair for your exception message, like the following image shows: ![Add resources to the default culture](media/add-resources-to-default-culture.jpg)</span></span>
1. <span data-ttu-id="d0738-130">フランス語用の新しいリソース ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="d0738-130">Add a new resource file for French.</span></span> <span data-ttu-id="d0738-131">*ExceptionMessages.fr-FR.resx* という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="d0738-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="d0738-132">例外メッセージの名前と値のペアを再び追加します。今回はフランス語の値を使用します。![fr-FR カルチャにリソースを追加する](media/add-resources-to-fr-culture.jpg)</span><span class="sxs-lookup"><span data-stu-id="d0738-132">Add a name/value pair for the exception message again, but with a French value: ![Add resources to the fr-FR culture](media/add-resources-to-fr-culture.jpg)</span></span>
1. <span data-ttu-id="d0738-133">プロジェクトをビルドすると、ビルド出力フォルダーには、サテライト アセンブリである *.dll* ファイルを含む *fr-FR* フォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d0738-133">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="d0738-134">次のようなコードを使用して例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="d0738-134">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > <span data-ttu-id="d0738-135">プロジェクト名が `TestProject` で、リソース ファイル *ExceptionMessages.resx* がプロジェクトの *Resources* フォルダー内にある場合、リソース ファイルの完全修飾名は `TestProject.Resources.ExceptionMessages` です。</span><span class="sxs-lookup"><span data-stu-id="d0738-135">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0738-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0738-136">See also</span></span>

- [<span data-ttu-id="d0738-137">ユーザー定義の例外を作成する方法</span><span class="sxs-lookup"><span data-stu-id="d0738-137">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="d0738-138">デスクトップ アプリケーションに対するサテライト アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="d0738-138">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="d0738-139">base (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d0738-139">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="d0738-140">this (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d0738-140">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
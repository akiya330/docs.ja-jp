---
ms.openlocfilehash: 4c676a185ff4a7a825acb059bf0a5842ca3922fc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394014"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="7034b-101">ターゲット フレームワーク: .NET Framework のサポートが廃止されました</span><span class="sxs-lookup"><span data-stu-id="7034b-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="7034b-102">ASP.NET Core 3.0 以降、.NET Framework はサポート対象外のターゲット フレームワークになりました。</span><span class="sxs-lookup"><span data-stu-id="7034b-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7034b-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="7034b-103">Change description</span></span>

<span data-ttu-id="7034b-104">.NET Framework 4.8 は、.NET Framework の最後のメジャー バージョンです。</span><span class="sxs-lookup"><span data-stu-id="7034b-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="7034b-105">新しい ASP.NET Core アプリは .NET Core で構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7034b-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="7034b-106">.NET Core 3.0 リリース以降、ASP.NET Core 3.0 は .NET Core の一部になっていると考えることができます。</span><span class="sxs-lookup"><span data-stu-id="7034b-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="7034b-107">.NET Framework で ASP.NET Core を使用しているお客様は、[2.1 LTS リリース](https://www.microsoft.com/net/download/dotnet-core/2.1)を使用して完全にサポートされた状態で続行できます。</span><span class="sxs-lookup"><span data-stu-id="7034b-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="7034b-108">2\.1 のサポートとサービスは、2021 年 8 月 21 日まで継続されます。</span><span class="sxs-lookup"><span data-stu-id="7034b-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="7034b-109">[.NET サポート ポリシー](https://www.microsoft.com/net/platform/support-policy)に従い、この日付は LTS リリースの宣言から 3 年後です。</span><span class="sxs-lookup"><span data-stu-id="7034b-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="7034b-110">**.NET Framework での**  ASP.NET Core 2.1 パッケージのサポートは、[他のパッケージ ベースの ASP.NET フレームワークのサービス ポリシー](https://dotnet.microsoft.com/platform/support/policy/aspnet)と同様に、無制限に延長されます。</span><span class="sxs-lookup"><span data-stu-id="7034b-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="7034b-111">.NET Framework から .NET Core への移植の詳細については、[.NET Core への移植](~/docs/core/porting/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7034b-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="7034b-112">`Microsoft.Extensions` パッケージ (ログ記録、依存関係の挿入、構成など) と Entity Framework Core は影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="7034b-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="7034b-113">.NET Standard はそれらで引き続きサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7034b-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="7034b-114">この変更の目的の詳細については、[元のブログ記事](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7034b-114">For more information on the motivation for this change, see [the original blog post](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7034b-115">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="7034b-115">Version introduced</span></span>

<span data-ttu-id="7034b-116">3.0</span><span class="sxs-lookup"><span data-stu-id="7034b-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7034b-117">以前の動作</span><span class="sxs-lookup"><span data-stu-id="7034b-117">Old behavior</span></span>

<span data-ttu-id="7034b-118">ASP.NET Core アプリは .NET Core または .NET Framework で実行できました。</span><span class="sxs-lookup"><span data-stu-id="7034b-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7034b-119">新しい動作</span><span class="sxs-lookup"><span data-stu-id="7034b-119">New behavior</span></span>

<span data-ttu-id="7034b-120">ASP.NET Core アプリは .NET Core でのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="7034b-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7034b-121">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="7034b-121">Recommended action</span></span>

<span data-ttu-id="7034b-122">次のいずれかのアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="7034b-122">Take one of the following actions:</span></span>

- <span data-ttu-id="7034b-123">ASP.NET Core 2.1 でアプリを保持します。</span><span class="sxs-lookup"><span data-stu-id="7034b-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="7034b-124">アプリと依存関係を .NET Core に移行します。</span><span class="sxs-lookup"><span data-stu-id="7034b-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="7034b-125">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="7034b-125">Category</span></span>

<span data-ttu-id="7034b-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7034b-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7034b-127">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="7034b-127">Affected APIs</span></span>

<span data-ttu-id="7034b-128">なし</span><span class="sxs-lookup"><span data-stu-id="7034b-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
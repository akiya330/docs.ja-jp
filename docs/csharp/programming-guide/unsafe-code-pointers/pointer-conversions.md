---
title: ポインター変換 - C# プログラミング ガイド
description: ポインター変換について説明します。 暗黙的および明示的なポインター変換の表とコード例を確認し、使用可能なその他のリソースを参照してください。
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: c39be5cb52964abbea5bc5636c6fa74d8411a331
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382088"
---
# <a name="pointer-conversions-c-programming-guide"></a>ポインター変換 (C# プログラミング ガイド)
定義済みの暗黙的なポインター変換を次の表に示します。 暗黙的な変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。  
  
## <a name="implicit-pointer-conversions"></a>暗黙的なポインター変換  
  
|From|終了|  
|----------|--------|  
|任意のポインター型|void*|  
|null|任意のポインター型|  
  
 明示的なポインター変換は、暗黙的な変換がない場合に、キャスト式を使用して、変換を実行するために使用します。 次の表はこの変換についてまとめたものです。  
  
## <a name="explicit-pointer-conversions"></a>明示的なポインター変換  
  
|From|終了|  
|----------|--------|  
|任意のポインター型|その他のポインター型|  
|sbyte、byte、short、ushort、int、uint、long または ulong|任意のポインター型|  
|任意のポインター型|sbyte、byte、short、ushort、int、uint、long または ulong|  
  
## <a name="example"></a>例  
 次の例では、`int` へのポインターは `byte` へのポインターに変換されます。 ポインターは、変数の最下位バイト アドレスを指すことに注意してください。 `int` のサイズ (4 バイト) まで結果を連続してインクリメントする場合、変数の残りのバイトを表示することができます。  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ポインター型](pointer-types.md)
- [参照型](../../language-reference/keywords/reference-types.md)
- [値型](../../language-reference/builtin-types/value-types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed ステートメント](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)

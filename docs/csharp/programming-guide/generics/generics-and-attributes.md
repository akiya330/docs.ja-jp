---
title: ジェネリックと属性 - C# プログラミング ガイド
description: ジェネリック型に属性を適用する方法について説明します。 コード例を参照し、使用可能なその他のリソースを確認してください。
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 17556af2e1bc2963de953cea242d7000509acbcd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299878"
---
# <a name="generics-and-attributes-c-programming-guide"></a>ジェネリックと属性 (C# プログラミング ガイド)
属性は、非ジェネリック型の場合と同様に、ジェネリック型に適用できます。 属性の適用については、「[属性](../concepts/attributes/index.md)」を参照してください。  
  
 カスタム属性は、型引数が与えられないオープン ジェネリック型と、すべての型パラメーターに引数が与えられる、構築クローズ ジェネリック型のみ参照が許可されます。  
  
 次の例では、このカスタム属性が使用されています。  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 属性は、オープン ジェネリック型を参照できます。  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 適切な数のコンマを利用し、複数の型パラメーターを指定します。 この例では、`GenericClass2` には 2 つの型パラメーターがあります。  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 属性は、構築クローズ ジェネリック型を参照できます。  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 ジェネリック型パラメーターを参照する属性は、コンパイル時エラーを引き起こします。  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 ジェネリック型は <xref:System.Attribute> から継承できません。  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 実行時にジェネリック型または型パラメーターに関する情報を取得するには、<xref:System.Reflection> のメソッドを利用できます。 詳細については、「[ジェネリックとリフレクション](./generics-and-reflection.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ジェネリック](./index.md)
- [属性](../../../standard/attributes/index.md)

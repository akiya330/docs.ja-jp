---
title: '方法: TextBox コントロールにフォーカスを設定する'
description: Focus メソッドを使用して、Windows Presentation Foundation の TextBox コントロールにフォーカスを設定する方法について学習します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: e107c22a3c5b701e02cbc8506d10fa35ee15c79d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168052"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a>方法: TextBox コントロールにフォーカスを設定する
この例では、<xref:System.Windows.UIElement.Focus%2A> メソッドを使用して <xref:System.Windows.Controls.TextBox> コントロールにフォーカスを設定する方法を示します。  
  
## <a name="example"></a>例  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 例では、*tbFocusMe* という名前の単純な <xref:System.Windows.Controls.TextBox> コントロールを示します。  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.UIElement.Focus%2A> メソッドが呼び出され、*tbFocusMe*. という名前の <xref:System.Windows.Controls.TextBox> コントロールにフォーカスが設定されます。  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)

---
title: 在 XAML 設計工具中繫結至資料
description: 瞭解如何使用畫板和屬性視窗設定資料系結屬性，將資料系結至 XAMl 設計工具中的控制項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 6bf3bd24b4a232899c64f6c0ecd819b0fe0f83a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961309"
---
# <a name="walkthrough-bind-to-data-in-xaml-designer"></a>在 XAML 設計工具中繫結至資料

在 XAML 設計工具中，您可以使用畫板和 [屬性] 視窗，設定資料繫結屬性。 本逐步解說中的範例示範如何將資料繫結至控制項。 具體來說，本逐步解說示範如何建立具有 [DependencyProperty](xref:Windows.UI.Xaml.DependencyProperty) 且名為 `ItemCount` 的簡單購物車類別，然後將 `ItemCount` 屬性繫結至 [TextBlock](xref:Windows.UI.Xaml.Controls.TextBlock) 控制項的 **Text** 屬性。

## <a name="to-create-a-class-to-use-as-a-data-source"></a>若要建立類別以做為資料來源

1. 在 [檔案] 功能表上，依序選擇 [新增] 和 [專案] > 。

1. 在 [新增專案] 對話方塊中，選擇 [Visual C#] 或 [Visual Basic] 節點，並展開 [Windows 桌面] 節點，然後選擇 [WPF 應用程式] 範本。

1. 將專案命名為 **BindingTest**，然後選擇 [確定] 按鈕。

1. 開啟 **MainWindow.xaml.cs** (或 **MainWindow.xaml.vb**) 檔案並新增下列程式碼。 在 C# 中，於 `BindingTest` 命名空間內 (在檔案中最後一個右括號之前) 加入程式碼。 在 Visual Basic 中，只需加入新類別。

   ```csharp
   public class ShoppingCart : DependencyObject
   {
       public int ItemCount
       {
           get { return (int)GetValue(ItemCountProperty); }
           set { SetValue(ItemCountProperty, value); }
       }

       public static readonly DependencyProperty ItemCountProperty =
            DependencyProperty.Register("ItemCount", typeof(int),
            typeof(ShoppingCart), new PropertyMetadata(0));
   }
   ```

   ```vb
   Public Class ShoppingCart
       Inherits DependencyObject

       Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))
       Public Property ItemCount As Integer
           Get
               ItemCount = CType(GetValue(ItemCountProperty), Integer)
           End Get
           Set(value As Integer)
               SetValue(ItemCountProperty, value)
           End Set
       End Property
   End Class
   ```

   上述程式碼會使用 [PropertyMetadata](xref:Windows.UI.Xaml.PropertyMetadata) 物件將預設項目計數的值設為 0。

1. 在 [檔案] 功能表上，選擇 [建置] > [建置方案]。

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>若要將 ItemCount 屬性繫結至 TextBlock 控制項

1. 在方案總管中，開啟 **MainWindow.xaml** 的捷徑功能表，然後選擇 [檢視設計工具]。

1. 在 [工具箱] 中，選擇 [Grid](xref:Windows.UI.Xaml.Controls.Grid) 控制項，以將它新增至表單。

1. 選取 `Grid`，然後在 [屬性] 視窗中，選擇 **DataContext** 屬性旁邊的 [新增] 按鈕。

1. 在 [選取物件] 對話方塊中，確定已清除 [顯示所有組件] 核取方塊，並選擇 **BindingTest** 命名空間下的 **ShoppingCart**，然後選擇 [確定] 按鈕。

     下圖顯示已選取 **ShoppingCart** 的 [選取物件] 對話方塊。

     ![[選取物件] 對話方塊](../designers/media/blendselectobject.png)

1. 在 [工具箱] 中，選擇 `TextBlock` 控制項，以將它新增至表單。

1. 選取 `TextBlock` 控制項，並在 [屬性] 視窗中選擇 **Text** 屬性右邊的屬性標記，然後選擇 [建立資料繫結] (屬性標記看起來像個小方塊)。

1. 在 [建立資料繫結] 對話方塊的 [路徑] 方塊中，選擇 **ItemCount : (int32)** 屬性，然後選擇 [確定] 按鈕。

     下圖顯示已選取 **ItemCount** 屬性的 [建立資料繫結] 對話方塊。

     ![[建立資料繫結] 對話方塊](../designers/media/xaml_create_data_binding.png)

1. 按 **F5** 執行應用程式。

     `TextBlock` 控制項應顯示預設值 0 做為文字。

## <a name="see-also"></a>另請參閱

- [使用 XAML 設計工具建立 UI](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [[新增值轉換器] 對話方塊](/previous-versions/hh965588(v=vs.140))
---
title: "逐步解說：在 XAML 設計工具中繫結至資料 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.XamlDesigner.DataBinding
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 4e2192a7fbcf2491a0e131ee6d6df0ead16238fd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>逐步解說：在 XAML 設計工具中繫結至資料
在 XAML 設計工具中，您可以使用畫板和 [屬性] 視窗來設定資料繫結屬性。 本逐步解說中的範例示範如何將資料繫結至控制項。 具體來說，本逐步解說示範如何建立具有 [DependencyProperty](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) 且名為 `ItemCount` 的簡單購物車類別，然後將 `ItemCount` 屬性繫結至 [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) 控制項的 **Text** 屬性。  
  
### <a name="to-create-a-class-to-use-as-a-data-source"></a>建立要做為資料來源使用的類別  
  
1.  在 [檔案]  功能表上，依序選擇 [新增] 和 [專案] 。  
  
2.  在 [新增專案] 對話方塊中，選擇 [Visual C#] 或 [Visual Basic] 節點，並展開 [Windows 桌面] 節點，然後選擇 [WPF 應用程式] 範本。  
  
3.  將專案命名為 **BindingTest**，然後選擇 [確定] 按鈕。  
  
4.  開啟 MainWindow.xaml.cs (或 MainWindow.xaml.vb) 檔案並加入下列程式碼。 在 C# 中，將程式碼加入 `BindingTest` 命名空間中 (檔案中最後一個右括號之前)。 在 Visual Basic 中，只要加入新類別。  
  
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
  
     上述程式碼會使用 [PropertyMetadata](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx) 物件將預設項目計數的值設為 0。  
  
5.  在 [檔案] 功能表上，依序選擇 [建置] 和 [建置方案]。  
  
### <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>將 ItemCount 屬性繫結至 TextBlock 控制項  
  
1.  在方案總管中，開啟 MainWindow.xaml 的捷徑功能表，然後選擇 [設計工具檢視]。  
  
2.  在 [工具箱] 中，選擇 [Grid](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) 控制項，以將它新增至表單。  
  
3.  選取 `Grid`，然後在 [屬性] 視窗中，選擇 **DataContext** 屬性旁邊的 [新增] 按鈕。  
  
4.  在 [選取物件] 對話方塊中，確定已清除 [顯示所有組件] 核取方塊，並選擇 **BindingTest** 命名空間下的 **ShoppingCart**，然後選擇 [確定] 按鈕。  
  
     下圖顯示已選取 **ShoppingCart** 的 [選取物件] 對話方塊。  
  
     ![[選取物件] 對話方塊](../designers/media/blendselectobject.PNG "BlendSelectObject")  
  
5.  在 [工具箱] 中，選擇 `TextBlock` 控制項，以將它新增至表單。  
  
6.  選取 `TextBlock` 控制項，並在 [屬性] 視窗中選擇 **Text** 屬性右邊的屬性標記，然後選擇 [建立資料繫結]  (屬性標記看起來像個小方塊)。  
  
7.  在 [建立資料繫結] 對話方塊的 [路徑] 方塊中，選擇 **ItemCount : (int32)** 屬性，然後選擇 [確定] 按鈕。  
  
     下圖顯示已選取 **ItemCount** 屬性的 [建立資料繫結] 對話方塊。  
  
     ![[建立資料繫結] 對話方塊](../designers/media/xaml_create_data_binding.png "xaml_create_data_binding")  
  
8.  按下 F5 即可執行應用程式。  
  
     `TextBlock` 控制項應顯示預設值 0 做為文字。  
  
## <a name="see-also"></a>請參閱  
 [使用 XAML 設計工具建立 UI](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)   
 [[新增值轉換器] 對話方塊](https://msdn.microsoft.com/en-us/c5f3d110-a541-4b55-8bca-928f77778af8)
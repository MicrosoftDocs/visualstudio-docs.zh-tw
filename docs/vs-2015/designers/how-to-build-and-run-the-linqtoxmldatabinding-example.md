---
title: 作法：建置並執行 LinqToXmlDataBinding 範例 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bebaeba2cc6f74a3ddbf059ca802252ad0bab6cf
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696147"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>作法：建置並執行 LinqToXmlDataBinding 範例
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

這個主題顯示如何建立與建置 LinqToXmlDataBinding Visual Studio 專案，以及如何執行所產生的 LinqToXmlDataBinding Windows Presentation Foundation (WPF) 範例程式。  
  
 如需有關使用 Visual Studio 建立專案的詳細資訊，請參閱 [Visual Studio 應用程式開發](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68)。  
  
## <a name="creating-and-populating-the-project"></a>建立和填入專案  
  
#### <a name="to-create-the-starting-project"></a>若要建立起始專案  
  
1. 啟動 Visual Studio，然後建立名稱為 LinqToXmlDataBinding 的 C# WPF 應用程式。 該專案必須使用 .NET Framework 3.5 (或更新版本)。  
  
2. 如果尚未存在，加入下列 .NET 組件的專案參考：  
  
    - System.Data  
  
    - System.Data.DataSetExtensions  
  
    - System.Xml  
  
    - System.Xml.Linq  
  
3. 按下 **Ctnrl+Shift+B** 來建置解決方案，然後按下 **F5** 來執行。 專案的編譯應該沒有錯誤，而且應該當做一般 WPF 應用程式執行。  
  
#### <a name="to-add-custom-code-to-the-project"></a>若要將自訂程式碼加入至專案  
  
1. 在 [方案總管] 中，將原始程式檔 Window1.xaml 重新命名為 L2XDBForm.xaml。 相依的原始程式檔 Window1.xaml.cs 應該會自動重新命名為 L2XDBForm.xaml.cs。  
  
2. 將 L2XDBForm.xaml 檔案中找到的原始程式碼，以 [L2DBForm.xaml 原始程式碼](../designers/l2dbform-xaml-source-code.md)主題中的程式碼區段取代。 (利用 XAML 原始碼檢視來使用這個檔案)。  
  
3. 同樣地，將 L2XDBForm.xaml.cs 中的原始碼，以 [L2DBForm.xaml.cs 原始程式碼](../designers/l2dbform-xaml-cs-source-code.md)中找到的程式碼取代。  
  
4. 在 App.xaml 檔案中，將出現的所有字串 "Window1.xaml" 取代為 "L2XDBForm.xaml"。  
  
5. 按下 **Ctrl+Shift+B**，建置解決方案。  
  
## <a name="running-the-program"></a>執行程式  
 LinqToXmlDataBinding 程式可讓使用者檢視與管理儲存為內嵌 XML 項目之書籍的清單。  
  
#### <a name="to-run-the-program-and-view-the-book-list"></a>若要執行程式與檢視書籍清單  
  
1. 按下 **F5** (開始偵錯) 或 **Ctrl+F5** (啟動但不偵錯)，執行 LinqToXmlDataBinding。 應隨即顯示標題為 [使用 LINQ to XML 進行 WPF 資料繫結] 的程式視窗。  
  
2. 請注意 UI 的上方區段，其中會顯示代表書籍清單的原始 **XML**。 它會使用 WPF <xref:System.Windows.Controls.TextBlock> 控制項顯示，不會透過滑鼠或鍵盤啟用互動。  
  
3. 第二個垂直區段標示為 [書籍清單]，會將書籍顯示為純文字排序的清單。 它使用 <xref:System.Windows.Controls.ListBox> 控制項，可透過滑鼠或鍵盤進行選取。  
  
#### <a name="to-add-and-delete-books-from-the-list"></a>若要加入和刪除清單中的書籍  
  
1. 若要從清單刪除現有的書籍，請在 [書籍清單] 區段選取該書籍，然後按一下 [移除選取的書籍] 按鈕。 請注意，該書籍項目已同時從書籍和原始 XML 來源清單移除。  
  
2. 若要將新的書籍新增至清單，請在最後一個區段 [新增書籍] 的 [ID] 和 [值] <xref:System.Windows.Controls.TextBox> 控制項中輸入值，然後按一下 [新增書籍] 按鈕。 請注意，該書籍會同時附加到書籍的清單和 XML 清單中。 這個程式不會驗證輸入值。  
  
#### <a name="to-edit-an-existing-book-entry"></a>若要編輯現有的書籍項目  
  
1. 在第二個 [書籍清單] 區段中選取書籍項目。 其目前的值應該會顯示在第三個區段 [編輯選取的書籍] 中。  
  
2. 使用鍵盤編輯值。 只要任一個 <xref:System.Windows.Controls.TextBox> 控制項失去焦點，這些變更就會自動填入到 XML 原始碼和書籍清單。  
  
## <a name="see-also"></a>另請參閱  
 [使用 LINQ to XML 的 WPF 資料繫結範例](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [逐步解說：LinqToXmlDataBinding 範例](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Visual Studio 應用程式開發](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68)

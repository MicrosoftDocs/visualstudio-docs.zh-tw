---
title: 選擇工具箱項目、WPF 元件 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 773ecc04569850546f03fd0cdb68bfe1a81a79f9
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54835022"
---
# <a name="choose-toolbox-items-wpf-components"></a>選擇工具箱項目，WPF 元件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
[選擇工具箱項目] 對話方塊的這個索引標籤會顯示您的本機電腦上可用的 Windows Presentation Foundation (WPF) 控制項清單。 若要顯示這份清單，請從 [工具] 功能表，選取 [選擇工具箱項目] 以顯示 [選擇工具箱項目] 對話方塊，然後選取其 [WPF 元件] 索引標籤。若要排序上列元件，請選取任一資料行標題。  
  
- 如果選取了某個元件旁的核取方塊，[工具箱] 中會顯示該元件的圖示。  
  
  > [!TIP]
  >  若要將 WPF 控制項的執行個體新增至開啟供編輯的專案文件，請將其工具箱圖示拖曳至 [設計檢視] 介面上。 該元件的預設標記和程式碼已插入您的專案，您可以隨時進行修改。 如需詳細資訊，請參閱[如何：管理工具箱視窗](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)和[如何︰操作工具箱索引標籤](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)。  
  
- 如果清除了某個元件旁的核取方塊，則會從 [工具箱] 移除對應的圖示。  
  
  > [!NOTE]
  >  安裝在您電腦上的 .NET Framework 元件仍然可供使用，而不論 [工具箱] 中是否顯示其圖示。  
  
  [WPF 元件] 索引標籤中的欄位包含下列資訊：  
  
  名稱  
  列出您電腦登錄中項目之 WPF 控制項的名稱。  
  
  命名空間  
  顯示 [NIB：.NET Framework Class Library](http://msdn.microsoft.com/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) 命名空間的階層架構，該階層架構定義了元件的結構。 依此欄排序即可列出安裝在您電腦上之每個 .NET Framework 命名空間內的可用元件清單。  
  
  組件名稱  
  顯示 .NET Framework 組件的名稱，其中包含每個元件的命名空間。 依此欄排序即可列出安裝在您電腦上之每個 .NET Framework 組件中所包含的命名空間清單。  
  
  Directory  
  顯示 .NET Framework 組件的位置。 所有組件的預設位置為 [全域組件快取]。 如需全域組件快取的進一步資訊，請參閱[使用組件和全域組件快取](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433)。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **篩選**  
 根據您在文字方塊中提供的字串來篩選 WPF 控制項清單。 這會顯示四個欄位中的所有相符項。  
  
 **清除**  
 清除篩選字串。  
  
 **瀏覽**  
 開啟 [開啟舊檔] 對話方塊，該對話方塊可讓您巡覽至包含 WPF 控制項的組件。 請使用此選項載入不在全域組件快取中的組件。  
  
 **Language**  
 顯示包含所選 WPF 控制項之組件的當地語系化語言。  
  
## <a name="limitations"></a>限制  
 將自訂控制項或 <xref:System.Windows.Controls.UserControl> 新增至工具箱的限制如下。  
  
- 只適用於在目前專案外部定義的自訂控制項。  
  
- 當您將方案組態從「偵錯」變更為「發行」或從「發行」變更為「偵錯」時，不會正確更新。 這是因為參考不是專案參考，而是針對磁碟上之組件的參考。 如果控制項是目前方案的一部分，當您從「偵錯」變更為「發行」時，專案會繼續參考「偵錯」版本的控制項。  
  
  此外，如果將設計階段中繼資料套用至自訂控制項，而且此中繼資料指定 <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> 設定為 `false`，則此控制項不會出現在工具箱中。  
  
  您可以藉由對應控制項的命名空間和組件，直接在 XAML 檢視中參考控制項。 如需詳細資訊，請參閱[如何：將命名空間匯入 XAML](http://msdn.microsoft.com/6cda7c7a-369c-47dd-9c2d-13a35dcf737c)。  
  
## <a name="see-also"></a>請參閱  
 [選擇工具箱項目對話方塊 (Visual Studio)](http://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [工具箱](../../ide/reference/toolbox.md)   
 [如何︰在 WPF 應用程式中使用協力廠商 WPF 控制項](http://msdn.microsoft.com/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [WPF 設計工具](http://msdn.microsoft.com/c6c65214-8411-4e16-b254-163ed4099c26)

---
title: "選擇工具箱項目、WPF 元件 | Microsoft Docs"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8aaa76694a60aad5c8bfcc2dd6d26feac03ab6e1
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2017
---
# <a name="choose-toolbox-items-wpf-components"></a>選擇工具箱項目，WPF 元件
[選擇工具箱項目] 對話方塊的這個索引標籤會顯示您的本機電腦上可用的 Windows Presentation Foundation (WPF) 控制項清單。 若要顯示這份清單，請從 [工具] 功能表，選取 [選擇工具箱項目] 以顯示 [選擇工具箱項目] 對話方塊，然後選取其 [WPF 元件] 索引標籤。若要排序上列元件，請選取任一資料行標題。  

-   如果選取了某個元件旁的核取方塊，[工具箱] 中會顯示該元件的圖示。  

    > [!TIP]
    >  若要將 WPF 控制項的執行個體新增至開啟供編輯的專案文件，請將其工具箱圖示拖曳至 [設計檢視] 介面上。 該元件的預設標記和程式碼已插入您的專案，您可以隨時進行修改。 如需詳細資訊，請參閱[使用工具箱](../../ide/using-the-toolbox.md)。  

-   如果清除了某個元件旁的核取方塊，則會從 [工具箱] 移除對應的圖示。  

    > [!NOTE]
    >  安裝在您電腦上的 .NET Framework 元件仍然可供使用，而不論 [工具箱] 中是否顯示其圖示。  

[WPF 元件] 索引標籤中的欄位包含下列資訊：  

名稱  
列出您電腦登錄中項目之 WPF 控制項的名稱。  

命名空間  
顯示 [.NET Framework Class API](/dotnet/api/?view=netframework-4.7) 命名空間的階層，該階層定義元件的結構。 依此欄排序即可列出安裝在您電腦上之每個 .NET Framework 命名空間內的可用元件清單。  

組件名稱  
顯示 .NET Framework 組件的名稱，其中包含每個元件的命名空間。 依此欄排序即可列出安裝在您電腦上之每個 .NET Framework 組件中所包含的命名空間清單。  

Directory  
顯示 .NET Framework 組件的位置。 所有組件的預設位置為 [全域組件快取]。 如需全域組件快取的進一步資訊，請參閱[使用組件和全域組件快取](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac)。  

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
將自訂控制項或 <xref:System.Windows.Controls.UserControl> 新增至工具箱的限制如下：  

-   只適用於在目前專案外部定義的自訂控制項。  

-   當您將方案組態從「偵錯」變更為「發行」或從「發行」變更為「偵錯」時，不會正確更新。 這是因為參考不是專案參考，而是針對磁碟上之組件的參考。 如果控制項是目前方案的一部分，當您從「偵錯」變更為「發行」時，專案會繼續參考「偵錯」版本的控制項。  

此外，如果將設計階段中繼資料套用至自訂控制項，而且此中繼資料指定 <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> 設定為 `false`，則此控制項不會出現在工具箱中。  

您可以藉由對應控制項的命名空間和組件，直接在 XAML 檢視中參考控制項。  

## <a name="see-also"></a>請參閱  
[工具箱](../../ide/reference/toolbox.md)  
[WPF 使用者入門](../../designers/getting-started-with-wpf.md)

---
title: 選擇工具箱項目，WPF 元件
description: 瞭解如何使用 [WPF 元件] 索引標籤，顯示可在本機電腦上選取的 Windows Presentation Foundation 控制項。
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b9727d335607f15101222e40be193de2315b7dc
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871323"
---
# <a name="choose-toolbox-items-wpf-components"></a>選擇工具箱項目、WPF 元件

[選擇工具箱項目] 對話方塊的這個索引標籤會顯示您的本機電腦上可用的 Windows Presentation Foundation (WPF) 控制項清單。 若要顯示這份清單，請從 [**工具**] 功能表選取 **[選擇工具箱專案**]，以顯示 [**選擇工具箱專案**] 對話方塊，然後選取其 [ **WPF 元件**] 索引標籤。若要排序列出的元件，請選取任何資料行標題。

- 如果選取了某個元件旁的核取方塊，[工具箱] 中會顯示該元件的圖示。

    > [!TIP]
    > 若要將 WPF 控制項新增至開啟供編輯的專案文件，請將其 **工具箱** 圖示拖曳至 [設計檢視] 介面上。 該元件的預設標記和程式碼已插入您的專案，您可以隨時進行修改。 如需詳細資訊，請參閱[工具箱](../../ide/reference/toolbox.md)。

- 如果清除了某個元件旁的核取方塊，則會從 [工具箱] 移除對應的圖示。

    > [!NOTE]
    > 安裝在您電腦上的 .NET 元件會保持可供使用，無論其圖示是否顯示在 [工具箱] 中。

[WPF 元件] 索引標籤中的欄位包含下列資訊：

**Name**

列出您電腦登錄中項目之 WPF 控制項的名稱。

**Namespace**

顯示 [.NET API](/dotnet/api/?view=netframework-4.7&preserve-view=true) 命名空間的階層，其能定義元件的結構。 依此欄排序以列出安裝在您電腦上之每個 .NET 命名空間內的可用元件。

**元件名稱**

顯示 .NET 組件的名稱，其中包含每個元件的命名空間。 依此欄排序以列出安裝在您電腦上之每個 .NET 組件中所包含的命名空間。

**目錄**

顯示 .NET 組件的位置。 所有組件的預設位置為 [全域組件快取]。 如需全域組件快取的詳細資訊，請參閱[使用組件和全域組件快取](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac)。

## <a name="uielement-list"></a>UIElement 清單

### <a name="filter"></a>篩選

根據您在文字方塊中提供的字串來篩選 WPF 控制項清單。 這會顯示四個欄位中的所有相符項。

**清除**

清除篩選字串。

**瀏覽**

開啟 [開啟舊檔] 對話方塊，該對話方塊可讓您巡覽至包含 WPF 控制項的組件。 請使用此選項載入不在全域組件快取中的組件。

**語言**

顯示包含所選 WPF 控制項之組件的當地語系化語言。

## <a name="limitations"></a>限制

將自訂控制項或 <xref:System.Windows.Controls.UserControl> 新增至工具箱的限制如下：

- 只適用於在目前專案外部定義的自訂控制項。

- 當您將方案組態從「偵錯」變更為「發行」或從「發行」變更為「偵錯」時，不會正確更新。 這是因為參考不是專案參考，而是針對磁碟上之組件的參考。 如果控制項是目前方案的一部分，當您從「偵錯」變更為「發行」時，專案會繼續參考「偵錯」版本的控制項。

此外，如果將設計階段中繼資料套用至自訂控制項，而且此中繼資料指定將 [Microsoft.Windows.Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) 設定為 `false`，則此控制項不會出現在 [工具箱] 中。

您可以藉由對應控制項的命名空間和組件，直接在 XAML 檢視中參考控制項。

## <a name="see-also"></a>另請參閱

- [工具箱](../../ide/reference/toolbox.md)
- [開始使用 WPF](../../designers/getting-started-with-wpf.md)

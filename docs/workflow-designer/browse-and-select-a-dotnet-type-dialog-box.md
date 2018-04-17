---
title: 瀏覽並選取.NET 類型對話方塊 |Microsoft 文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 04aba24d3dffc96fb8e5288d74322258fa77ce19
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>瀏覽並選取 .NET 類型對話方塊

在**屬性**視窗、 對話方塊中或設計工具，例如變數設計工具中，當您選取**瀏覽型別...**從資料類型的清單，是**瀏覽並選取.NET 型別**對話方塊 （簡稱為 「 型別瀏覽器 」 是簡短形式）。 在這個對話方塊中，您可以從組件與專案的樹狀檢閱中選擇型別。

 有幾個使用者案例會採用這個對話方塊，包括下列：

-   設定變數或引數的型別時。

-   為泛型活動選取型別時。

-   在 <xref:System.Activities.Statements.TryCatch> 活動上加入 catch 時。

> [!NOTE]
> 型別瀏覽器可以顯示 Visual Basic 不規則陣列型別，而不是多維陣列型別。 請參閱[不規則陣列](http://go.microsoft.com/fwlink/?LinkId=195226)和[多維陣列](http://go.microsoft.com/fwlink/?LinkId=195227)如需詳細資訊。

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>從型別瀏覽器選取值或參考型別

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>若要從型別瀏覽器選取值或參考型別

1.  在**型別名稱**方塊中，輸入您想要使用的型別名稱。

2.  執行下列任一步驟：

    -   一旦您想要使用的型別名稱會出現在樹狀目錄中**型別名稱**方塊中，按兩下該型別加以選取。

    -   輸入中的字元足以**型別名稱**方塊來唯一識別您想要使用，然後按 enter 鍵來選取類型的型別

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>若要從型別瀏覽器選取泛型型別

1.  在**型別名稱**方塊中，輸入您想要使用的類型。

2.  一旦您想要使用的型別名稱會出現在樹狀目錄中**型別名稱**方塊中，按一下来選取，下拉式清單方塊的型別就會出現。

     選取您要用來關閉下拉式清單方塊中中的泛型，然後按一下類型**確定**。

## <a name="types-displayed-in-the-type-browser"></a>型別瀏覽器中顯示的型別
 型別瀏覽器中顯示的型別，可能會因型別瀏覽器啟動的方式而異。 如果型別瀏覽器已啟動工作流程專案中，內部**vs2010**、 根據預設所有參考的組件中的類型和參考的專案會顯示。 如果型別瀏覽器中啟動外部**vs2010**專案系統 （例如，如同在重新裝載工作流程應用程式或獨立的工作流程檔案中），則預設會顯示所有 AppDomain 中載入的組件的型別.

 活動設計工具開發人員可以篩選型別瀏覽器中的型別。 對於任何特定活動，可以只顯示一個子集的型別。 例如，在 <xref:System.Activities.Statements.TryCatch> 活動中，型別瀏覽器中只顯示衍生自 <xref:System.Exception> 的型別。

## <a name="filtering-search-results-in-the-type-browser"></a>篩選型別瀏覽器中的搜尋結果
 中的型別清單**型別名稱**方塊會縮短您輸入更多字元尋找符合項目。 在已篩選清單中，只會顯示其完整限定名稱開頭是您輸入字串的型別，或是其簡短名稱開頭是您輸入字串的型別。

 例如: 

1.  輸入**作業**符合<xref:System.OperationCanceledException>但不是<xref:System.InvalidOperationException>。 若要符合 <xref:System.InvalidOperationException>，一開始請輸入 System.I 或 Invalid。

2.  輸入**泛型**符合<xref:System.GenericUriParser>但不是會在輸入<xref:System.Collections.Generic>命名空間。 若要搜尋 <xref:System.Collections.Generic> 命名空間中的型別，請輸入命名空間的完整限定名稱。

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>使用型別瀏覽器對話方塊選取服務合約
 選取服務合約型別時，型別瀏覽器只顯示具有 <xref:System.ServiceModel.ServiceContractAttribute> 屬性的型別。

## <a name="see-also"></a>另請參閱

- [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)
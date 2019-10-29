---
title: 工作流程設計工具-流覽並選取 .NET 類型對話方塊
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2efea8f23e42b9f4839c8a1ae0d74248738b9cf4
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985344"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>瀏覽並選取 .NET 類型對話方塊

在 [**屬性**] 視窗、對話方塊或設計工具（例如 [變數設計工具]）中，當您選取 [從資料類型清單**流覽類型]** 時，會是 [**流覽並選取 .net 類型**] 對話方塊（在縮寫形式中稱為「類型」瀏覽器」）。 在這個對話方塊中，您可以從組件與專案的樹狀檢視中選擇型別。

有幾個使用者案例會採用這個對話方塊，包括下列：

- 設定變數或引數的型別時。

- 為泛型活動選取型別時。

- 在 <xref:System.Activities.Statements.TryCatch> 活動上加入 catch 時。

> [!NOTE]
> 型別瀏覽器可以顯示 Visual Basic 不規則陣列型別，而不是多維陣列型別。 如需詳細資訊，請參閱[不規則陣列](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90))和[多維陣列](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90))。

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>從型別瀏覽器選取值或參考型別

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>若要從型別瀏覽器選取值或參考型別

1. 在 [**類型名稱**] 方塊中，輸入您要使用之類型的名稱。

2. 執行下列任一步驟：

    - 一旦您要使用的型別名稱出現在 [**型別名稱**] 方塊的樹狀結構中，請按兩下該型別來選取它。

    - 在 [**類型名稱**] 方塊中輸入足夠的字元，以唯一識別您想要使用的類型，然後按 enter 鍵以選取類型

### <a name="to-select-a-generic-type-from-the-type-browser"></a>若要從型別瀏覽器選取泛型型別

1. 在 [**類型名稱**] 方塊中，輸入您要使用之類型的名稱。

2. 一旦您要使用的型別名稱出現在 [**型別名稱**] 方塊的樹狀結構中，請按一下該型別來選取它，這樣就會出現下拉式方塊。

     從下拉式方塊中選取您要用來關閉 [一般] 的類型，然後按一下 **[確定]** 。

## <a name="types-displayed-in-the-type-browser"></a>型別瀏覽器中顯示的型別

型別瀏覽器中顯示的型別，可能會因型別瀏覽器啟動的方式而異。 如果類型瀏覽器是從**vs2010**內的工作流程專案啟動，則預設會顯示參考元件和參考專案中的所有類型。 如果類型瀏覽器是從**vs2010**專案系統的外部啟動（例如在重新裝載工作流程應用程式或獨立工作流程檔案中），則會顯示從 AppDomain 載入之所有元件中的類型。

活動設計工具開發人員可以篩選型別瀏覽器中的型別。 對於任何特定活動，可以只顯示一個子集的型別。 例如，在 <xref:System.Activities.Statements.TryCatch> 活動中，型別瀏覽器中只顯示衍生自 <xref:System.Exception> 的型別。

## <a name="filtering-search-results-in-the-type-browser"></a>篩選型別瀏覽器中的搜尋結果

當您輸入更多字元來尋找相符項時，[**類型名稱**] 方塊中的類型清單會變短。 只有 fullyqualified 名稱開頭為您所輸入字串的類型，或以您所輸入的字串開頭的類型，才會出現在篩選清單中。

例如:

1. 輸入**作業**會符合 <xref:System.OperationCanceledException>，但不會 <xref:System.InvalidOperationException>。 若要符合 <xref:System.InvalidOperationException>，一開始請輸入 System.I 或 Invalid。

2. 輸入**泛型**符合 <xref:System.GenericUriParser>，但不是 <xref:System.Collections.Generic> 命名空間中的類型。 若要搜尋 <xref:System.Collections.Generic> 命名空間中的類型，請輸入命名空間的完整名稱。

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>使用型別瀏覽器對話方塊選取服務合約

選取服務合約型別時，型別瀏覽器只顯示具有 <xref:System.ServiceModel.ServiceContractAttribute> 屬性的型別。

## <a name="see-also"></a>請參閱

- [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)
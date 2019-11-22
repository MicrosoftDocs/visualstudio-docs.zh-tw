---
title: 流覽並選取 .NET 類型對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8e25ad181202a2c7994c116e2220426ca3d8509
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297619"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>瀏覽並選取 .NET 類型對話方塊
當您選取 [**流覽類型 ...** ] 時，在 [**屬性**] 視窗中，對話方塊或設計工具（例如變數設計工具） 從資料類型清單中，是 [**流覽並選取 .Net 類型**] 對話方塊（在縮寫格式中稱為「類型瀏覽器」）。 在這個對話方塊中，您可以從組件與專案的樹狀檢視中選擇型別。

 有幾個使用者案例會採用這個對話方塊，包括下列：

- 設定變數或引數的型別時。

- 為泛型活動選取型別時。

- 在 <xref:System.Activities.Statements.TryCatch> 活動上加入 catch 時。

> [!NOTE]
> 型別瀏覽器可以顯示 Visual Basic 不規則陣列型別，而不是多維陣列型別。 如需詳細資訊，請參閱[不規則陣列](https://go.microsoft.com/fwlink/?LinkId=195226)和[多維陣列](https://go.microsoft.com/fwlink/?LinkId=195227)。

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>從型別瀏覽器選取值或參考型別

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>若要從型別瀏覽器選取值或參考型別

1. 在 [**型別名稱**] 方塊中，輸入您要使用之型別的名稱。

2. 請執行下列其中一項動作：

    - 一旦您要使用的型別名稱顯示在 [**型別名稱**] 方塊中，請按兩下該型別以選取。

    - 在 [**型別名稱**] 方塊中輸入足以識別您要使用之型別的唯一名稱，然後按 Enter 鍵選取該型別。

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>若要從型別瀏覽器選取泛型型別

1. 在 [**型別名稱**] 方塊中，輸入您要使用之型別的名稱。

2. 一旦您要使用的型別名稱顯示在 [**型別名稱**] 方塊中，請按一下該型別加以選取，下拉式方塊就會出現。

     選取您要使用的型別，即可關閉下拉式方塊中的泛型，然後按一下 [**確定**]。

## <a name="types-displayed-in-the-type-browser"></a>型別瀏覽器中顯示的型別
 型別瀏覽器中顯示的型別，可能會因型別瀏覽器啟動的方式而異。 如果型別瀏覽器是從 **vs2010** 內部某個工作流程專案啟動，預設就會顯示參考組件與參考專案中的所有型別。 如果型別瀏覽器是從 **vs2010** 專案系統外部 (例如在重新裝載的工作流程應用程式中，或是在獨立工作流程檔案中) 啟動，預設就會顯示 AppDomain 中載入之所有組件的型別。

 活動設計工具開發人員可以篩選型別瀏覽器中的型別。 對於任何特定活動，可以只顯示一個子集的型別。 例如，在 <xref:System.Activities.Statements.TryCatch> 活動中，型別瀏覽器中只顯示衍生自 <xref:System.Exception> 的型別。

## <a name="filtering-search-results-in-the-type-browser"></a>篩選型別瀏覽器中的搜尋結果
 在您輸入更多字元尋找符合型別的同時，[**型別名稱**] 方塊中的型別清單會縮短。 在已篩選清單中，只會顯示其完整限定名稱開頭是您輸入字串的型別，或是其簡短名稱開頭是您輸入字串的型別。

 例如：

1. 輸入 **Operation** 會與 <xref:System.OperationCanceledException> 相符，但不會有 <xref:System.InvalidOperationException>。 若要符合 <xref:System.InvalidOperationException>，一開始請輸入 System.I 或 Invalid。

2. 輸入 **Generic** 會與 <xref:System.GenericUriParser> 相符，但不會有 <xref:System.Collections.Generic> 命名空間中的型別。 若要搜尋 <xref:System.Collections.Generic> 命名空間中的型別，請輸入命名空間的完整限定名稱。

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>使用型別瀏覽器對話方塊選取服務合約
 選取服務合約型別時，型別瀏覽器只顯示具有 <xref:System.ServiceModel.ServiceContractAttribute> 屬性的型別。

## <a name="see-also"></a>另請參閱
 [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)
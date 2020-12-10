---
title: 瀏覽並選取 .NET 類型對話方塊
description: 瞭解如何使用 [流覽並選取 .NET 型別] 對話方塊，從工作流程設計工具中的元件和專案樹狀檢視中選擇型別。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9c479cbad884a8a21197c945f8f6f1ae13947991
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995482"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>瀏覽並選取 .NET 類型對話方塊

在 [ **屬性** ] 視窗、對話方塊或設計工具（例如變數設計工具）中，當您從資料類型清單中選取 **[流覽類型]** 時，[ **流覽並選取 .net 類型** ] 對話方塊 (在 [類型瀏覽器] ) 的縮寫形式中參考。 在這個對話方塊中，您可以從組件與專案的樹狀檢視中選擇型別。

有幾個使用者案例會採用這個對話方塊，包括下列：

- 設定變數或引數的型別時。

- 為泛型活動選取型別時。

- 在 <xref:System.Activities.Statements.TryCatch> 活動上加入 catch 時。

> [!NOTE]
> 型別瀏覽器可以顯示 Visual Basic 不規則陣列型別，而不是多維陣列型別。 請參閱 [不規則陣列](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) 和 [多維陣列](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90)) 以取得詳細資料。

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>從型別瀏覽器選取值或參考型別

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>若要從型別瀏覽器選取值或參考型別

1. 在 [ **類型名稱** ] 方塊中，輸入您要使用之類型的名稱。

2. 請執行下列其中一項：

    - 一旦您要使用的型別名稱顯示在 [ **型別名稱** ] 方塊中的樹狀結構中，請按兩下該型別加以選取。

    - 在 [ **類型名稱** ] 方塊中輸入足夠的字元來唯一識別您要使用的類型，然後按 enter 鍵以選取類型

### <a name="to-select-a-generic-type-from-the-type-browser"></a>若要從型別瀏覽器選取泛型型別

1. 在 [ **類型名稱** ] 方塊中，輸入您要使用之類型的名稱。

2. 一旦您要使用的型別名稱出現在 [ **型別名稱** ] 方塊中的樹狀結構中，請按一下該型別加以選取，讓下拉式方塊出現。

     從下拉式方塊中選取您要用來關閉 [一般] 的類型，然後按一下 **[確定]**。

## <a name="types-displayed-in-the-type-browser"></a>型別瀏覽器中顯示的型別

型別瀏覽器中顯示的型別，可能會因型別瀏覽器啟動的方式而異。 如果已從 **vs2010** 內的工作流程專案啟動型別瀏覽器，則預設會顯示參考元件和參考專案中的所有類型。 如果在 **vs2010** 專案系統之外啟動型別瀏覽器 (例如在重新裝載工作流程應用程式中，或是在獨立的) 工作流程檔案中，則預設會顯示在 AppDomain 中載入之所有元件的類型。

活動設計工具開發人員可以篩選型別瀏覽器中的型別。 對於任何特定活動，可以只顯示一個子集的型別。 例如，在 <xref:System.Activities.Statements.TryCatch> 活動中，型別瀏覽器中只顯示衍生自 <xref:System.Exception> 的型別。

## <a name="filtering-search-results-in-the-type-browser"></a>篩選型別瀏覽器中的搜尋結果

當您輸入更多字元來尋找相符的字元時，[ **型別名稱** ] 方塊中的類型清單會變得較短。 只有 fullyqualified 名稱是以您輸入的字串開頭的型別，或簡短名稱以您輸入的字串開頭的類型，才會出現在篩選清單中。

例如：

1. 輸入 **作業** 相符 <xref:System.OperationCanceledException> ，但不符合 <xref:System.InvalidOperationException> 。 若要符合 <xref:System.InvalidOperationException>，一開始請輸入 System.I 或 Invalid。

2. 輸入 **泛型** 相符專案 <xref:System.GenericUriParser> ，但不是 <xref:System.Collections.Generic> 命名空間中的類型。 若要在命名空間中搜尋類型 <xref:System.Collections.Generic> ，請輸入命名空間的完整名稱。

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>使用型別瀏覽器對話方塊選取服務合約

選取服務合約型別時，型別瀏覽器只顯示具有 <xref:System.ServiceModel.ServiceContractAttribute> 屬性的型別。

## <a name="see-also"></a>另請參閱

- [使用活動設計工具](control-flow-activity-designers.md)

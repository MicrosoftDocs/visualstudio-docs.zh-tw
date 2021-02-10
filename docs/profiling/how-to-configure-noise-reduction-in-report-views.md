---
title: 在報表檢視中設定減少雜訊 | Microsoft Docs
description: 使用修剪和折迭（預設為啟用）來減少雜訊，並讓報表中的效能問題更加顯著。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5037cf0184608829d5a86d736bead5b61f5172c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969330"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>如何：在報表檢視中設定減少雜訊
效能報告可透過限制 [呼叫樹狀圖] 檢視和 [配置] 檢視中呈現的資料量來減少雜訊。 藉由減少雜訊，效能問題將更為顯著。 在分析效能報告時，這一點非常有用。

 減少雜訊組態選項包括下列設定︰

- **修剪** 分析報表時，檢視將省略落在您設定的值和臨界值中的函式，如後續的修剪程序所述。 修剪預設為啟用。

- **折疊** 如果啟用折疊，將合併符合您設定之設定的路徑上的連續函式，如後續的折疊程序所述。 折疊預設為啟用。

### <a name="to-configure-trimming-for-a-performance-report"></a>設定修剪效能報告

1. 當產生的報告中顯示 [呼叫樹狀圖] 檢視或 [配置] 檢視時，在 [開發人員] 功能表上，按一下 [程式碼剖析工具]，然後按一下 [減少雜訊選項]。

     [減少雜訊] 對話方塊隨即顯示。

2. 若要啟用修剪，請依照以下步驟進行：

    1. 選取 [啟用修剪]。 這是預設值。

        > [!NOTE]
        > 如果已啟用減少雜訊，資訊列會顯示在報告中。 如需詳細資訊，請參閱[呼叫樹狀圖檢視](../profiling/call-tree-view.md)和[配置檢視](../profiling/dotnet-memory-allocations-view.md)。

    2. 使用 [值] 下拉式清單並選擇適用的設定以設定值設定。

    3. 在 [臨界值] 文字方塊中輸入一個百分比值，以設定需要的臨界值設定。

    4. 若要在產生的報告中啟用減少雜訊警告，請選取 [啟用減少雜訊時顯示警告]。 這是預設值。

3. 若要停用修剪，請清除 [啟用修剪]。

4. 按一下 [確定]  。

### <a name="to-configure-folding-for-a-performance-report"></a>設定折疊效能報告

1. 在 [開發人員] 功能表上，按一下 [程式碼剖析工具]，然後按一下 [減少雜訊選項]。

     [減少雜訊] 對話方塊隨即顯示。

2. 若要啟用摺疊，請依照以下步驟進行：

    1. 選取 [啟用摺疊]。 這是預設值。

        > [!NOTE]
        > 如果已啟用減少雜訊，資訊列會顯示在報告中。 如需詳細資訊，請參閱[呼叫樹狀圖檢視](../profiling/call-tree-view.md)和[配置檢視](../profiling/dotnet-memory-allocations-view.md)。

    2. 使用 [值] 下拉式清單並選取適用的設定以設定值設定。

    3. 在 [臨界值] 文字方塊中輸入一個百分比值，以設定需要的臨界值設定。

    4. 若要在產生的報告中啟用減少雜訊警告，請選取 [啟用減少雜訊時顯示警告]。 這是預設值。

3. 若要停用摺疊，請清除 [啟用摺疊]。

4. 按一下 [確定]  。

## <a name="see-also"></a>另請參閱
- [自訂效能工具報表檢視](../profiling/customizing-performance-tools-report-views.md)
- [如何：從檢測排除或包含精簡函式](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)
- [呼叫樹狀圖檢閱](../profiling/call-tree-view.md)
- [配置檢視](../profiling/dotnet-memory-allocations-view.md)

---
title: 儲存和匯出效能工具資料 | Microsoft Docs
description: 瞭解如何將剖析資料的已篩選或未篩選視圖儲存 ( .vsp) 檔案做為分析的報表 ( .vsps) 檔。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fa43d324f23958c9dc9b72447527ecd035e99c53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950100"
---
# <a name="save-and-export-performance-tools-data"></a>儲存和匯出效能工具資料
本文描述如何儲存和匯出效能資料檔案。

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>如何︰將效能資料檔案儲存為分析的報告檔案
 您可以儲存分析資料 ( 的已篩選或未篩選的觀點。將 *.vsp*) 檔案視為分析過的報表 (。*.vsps*) 檔。 您可以在 [報表] 視圖視窗中查看分析的報表檔案，而且遠小於原始的報表檔案。*.vsp* 檔案。 但是，您不能將篩選套用到的資料。*.vsps* 檔案。 您可以從效能總管建立分析的報告檔案，而不需要在整合式開發環境 (IDE) 中開啟檔案，或者您可以開啟和篩選。*.vsp* 檔案，然後儲存結果。

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>從 [效能總管] 儲存分析的效能報告

1. 在 [報表] 下，以滑鼠右鍵按一下您想要分析的分析資料檔案，然後按一下 [儲存分析過的項目] 。

2. 在 [儲存分析的資料]  對話方塊中指定目錄，接著輸入檔案名稱。

3. 按一下 [儲存]。

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>從 [報告] 檢視視窗儲存分析的效能報告

1. 開啟 [分析資料] (。[報表] 窗格中的 [ *.vsp*) 檔案]。

2. (選用) 將篩選套用至資料。 如需詳細資訊，請參閱 [效能報表檢視篩選](../profiling/performance-report-view-filter.md)。

3. 按一下 [報表] 檢視視窗工具列上的 [儲存分析過的項目]  。

4. 在 [儲存分析的資料]  對話方塊中指定目錄，接著輸入檔案名稱。

5. 按一下 [儲存]。

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>如何︰將分析工具報告匯出至 .xml 或 .csv 檔案
 您可以從匯出一或多個報表檢視。*.vsp* 檔案或。*.vsps* 分析資料檔（以逗號分隔或 XML 檔案）。 您可於匯出前，在 [報告] 檢視視窗中篩選資料，或是從 [效能總管]  視窗匯出整個資料檔案的報告檢視。

> [!NOTE]
> 您也可以從 [報表] 檢視視窗將選取的資料列作為定位字元分隔值進行複製並貼上。

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>從 [效能總管] 視窗匯出效能報告

1. 在 [效能總管] 中，選取報表然後以滑鼠右鍵按一下並選取 [匯出] 。

     [匯出報告]  對話方塊隨即出現。

2. 選取您想要匯出的報告檢視。

3. 在 [Prefix report with] (在報告前面加入) 下，指定您想要新增至報告名稱的前置詞。

4. 在 [匯出的報告位置] 下，指定目錄。

5. 在 [匯出的報告格式] 下，選取 [逗點分隔] (\*.csv\) 或 [XML 資料] (\*.xml\)。

6. 按一下 [匯出]  。

     每個報表檢視都會儲存在名為 _ 的個別檔案中 \<prefix> \<report view name> 。\<csv&#124;xml>

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>從 [報告] 檢視視窗匯出效能報告

1. 開啟。報表檢視視窗中的 *.vsp* 檔案。

2. (選用) 將篩選套用至資料。 如需詳細資訊，請參閱 [效能報表檢視篩選](../profiling/performance-report-view-filter.md)。

3. 按一下 [報表] 檢視視窗工具列上的 [匯出報告]  。

4. 選取您想要匯出的報告檢視。

5. 在 [Prefix report with] (在報告前面加入) 下，指定您想要新增至報告名稱的前置詞。

6. 在 [匯出的報告位置] 下，指定目錄。

7. 在 [ **匯出的報告格式**] 下，選取 (逗號分隔)  (\* .CSV) 或 xml 資料 (.xml \*) 。

8. 按一下 [匯出]  。

     每個報表檢視都會儲存在名為 _ 的個別檔案中 \<prefix> \<report view name> 。\<csv&#124;xml>

## <a name="see-also"></a>另請參閱
- [效能總管](../profiling/performance-explorer.md)
- [分析效能工具資料](../profiling/analyzing-performance-tools-data.md)
- [比較效能資料檔案](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)

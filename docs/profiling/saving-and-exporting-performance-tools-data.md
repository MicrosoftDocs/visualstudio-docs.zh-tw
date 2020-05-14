---
title: 儲存和匯出效能工具資料 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 729dc2e28446420dd2590e132b7ec8a5444fcb9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773895"
---
# <a name="save-and-export-performance-tools-data"></a>儲存和匯出效能工具資料
本文描述如何儲存和匯出效能資料檔案。

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>如何︰將效能資料檔案儲存為分析的報告檔案
 您可以保存分析資料的篩選視圖或未篩選視圖 （。*vsp*） 檔作為分析報告 （.*vps*） 檔。 可以在"報表"視圖視窗中查看分析的報告檔，並且明顯小於原始報表檔。*vsp*檔。 但是，不能將篩選器應用於 的資料。*vsps*檔。 您可以在性能資源管理器中創建分析的報告檔，而無需在整合式開發環境 （IDE） 中打開該檔，也可以打開和篩選 。*vsp*檔，然後保存結果。

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>從 [效能總管] 儲存分析的效能報告

1. 在 [報表] **** 下，以滑鼠右鍵按一下您想要分析的分析資料檔案，然後按一下 [儲存分析過的項目] ****。

2. 在 [儲存分析的資料] **** 對話方塊中指定目錄，接著輸入檔案名稱。

3. 按一下"**保存"。**

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>從 [報告] 檢視視窗儲存分析的效能報告

1. 打開分析資料 （。*"* 報表"視圖視窗中的檔為 vsp ）。

2. (選用) 將篩選套用至資料。 有關詳細資訊，請參閱[性能報表檢視篩選器](../profiling/performance-report-view-filter.md)。

3. 按一下 [報表] 檢視視窗工具列上的 [儲存分析過的項目] **** 。

4. 在 [儲存分析的資料] **** 對話方塊中指定目錄，接著輸入檔案名稱。

5. 按一下"**保存"。**

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>如何︰將分析工具報告匯出至 .xml 或 .csv 檔案
 可以從 匯出一個或多個報表檢視。*vsp*檔或 。*vsps*將資料檔案分析為逗號分隔符號或 XML 檔。 您可於匯出前，在 [報告] 檢視視窗中篩選資料，或是從 [效能總管] **** 視窗匯出整個資料檔案的報告檢視。

> [!NOTE]
> 您也可以從 [報表] 檢視視窗將選取的資料列作為定位字元分隔值進行複製並貼上。

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>從 [效能總管] 視窗匯出效能報告

1. 在 [效能總管] **** 中，選取報表然後以滑鼠右鍵按一下並選取 [匯出] ****。

     [匯出報告] **** 對話方塊隨即出現。

2. 選取您想要匯出的報告檢視。

3. 在 [Prefix report with] (在報告前面加入) **** 下，指定您想要新增至報告名稱的前置詞。

4. 在 [匯出的報告位置] **** 下，指定目錄。

5. 在 [匯出的報告格式]**** 下，選取 [逗點分隔] (\*.csv\) 或 [XML 資料] (\*.xml\)。

6. 按一下 [匯出]****。

     每個報告檢視都會儲存到個別的檔案，稱為 \<前置詞>_\<報告檢視名稱>.\<csv&#124;xml>。

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>從 [報告] 檢視視窗匯出效能報告

1. 打開 。"報表"視圖視窗中的*vsp*檔。

2. (選用) 將篩選套用至資料。 有關詳細資訊，請參閱[性能報表檢視篩選器](../profiling/performance-report-view-filter.md)。

3. 按一下 [報表] 檢視視窗工具列上的 [匯出報告] **** 。

4. 選取您想要匯出的報告檢視。

5. 在 [Prefix report with] (在報告前面加入) **** 下，指定您想要新增至報告名稱的前置詞。

6. 在 [匯出的報告位置] **** 下，指定目錄。

7. 在**匯出的報告格式**下，選擇（逗號分隔）（.csv）\*或 XML 資料\*（.xml）。

8. 按一下 [匯出]****。

     每個報告檢視都會儲存到個別的檔案，稱為 \<前置詞>_\<報告檢視名稱>.\<csv&#124;xml>。

## <a name="see-also"></a>另請參閱
- [效能總管](../profiling/performance-explorer.md)
- [分析性能工具資料](../profiling/analyzing-performance-tools-data.md)
- [比較效能資料檔](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)

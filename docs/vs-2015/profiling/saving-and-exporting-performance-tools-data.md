---
title: 儲存和匯出效能工具資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3be6d5d732e5cbb2050c68ac8c7db722c3f709f2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428097"
---
# <a name="saving-and-exporting-performance-tools-data"></a>儲存和匯出報告效能工具資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題描述如何儲存和匯出效能資料檔案。  
  
## <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> 如何︰將效能資料檔案儲存為分析的報告檔案  
 您可以將分析資料 (.vsp) 檔案的已篩選或未篩選檢視儲存為分析的報告 (.vsps) 檔案。 分析的報告檔案可以在 [報表] 檢視視窗中檢視，且比原始 .vsp 檔案小得多。 不過，您無法將篩選套用至 .vsps 檔案的資料。 您可以從 [效能總管] 建立分析的報告檔案，而不須在整合式的開發環境 (IDE) 中開啟檔案，或者您可以開啟並篩選 .vsp 檔案，然後儲存結果。  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>從 [效能總管] 儲存分析的效能報告  
  
1. 在 [報表] 下，以滑鼠右鍵按一下您想要分析的分析資料檔案，然後按一下 [儲存分析過的項目] 。  
  
2. 在 [儲存分析的資料]  對話方塊中指定目錄，接著輸入檔案名稱。  
  
3. 按一下 [儲存]   
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>從 [報告] 檢視視窗儲存分析的效能報告  
  
1. 在 [報告] 檢視視窗中開啟分析資料 (.vsp) 檔案。  
  
2. (選用) 將篩選套用至資料。 如需詳細資訊，請參閱[效能報告檢視篩選](../profiling/performance-report-view-filter.md)。  
  
3. 按一下 [報表] 檢視視窗工具列上的 [儲存分析過的項目]  。  
  
4. 在 [儲存分析的資料]  對話方塊中指定目錄，接著輸入檔案名稱。  
  
5. 按一下 [儲存]   
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>如何︰將分析工具報告匯出至 .Xml 或 .Csv 檔案  
 您可以從 .vsp 檔案或 .vsps 分析資料檔案將一或多個報告檢視匯出為逗點分隔的檔案或 XML 檔案。 您可於匯出前，在 [報告] 檢視視窗中篩選資料，或是從 [效能總管]  視窗匯出整個資料檔案的報告檢視。  
  
> [!NOTE]
> 您也可以從 [報表] 檢視視窗將選取的資料列作為定位字元分隔值進行複製並貼上。  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>從 [效能總管] 視窗匯出效能報告  
  
1. 在 [效能總管] 中，選取報表然後以滑鼠右鍵按一下並選取 [匯出] 。  
  
     [匯出報告]  對話方塊隨即出現。  
  
2. 選取您想要匯出的報告檢視。  
  
3. 在 [Prefix report with] (在報告前面加入) 下，指定您想要新增至報告名稱的前置詞。  
  
4. 在 [匯出的報告位置] 下，指定目錄。  
  
5. 在 [匯出的報告格式] 下，選取 [逗點分隔] (*.csv) 或 [XML 資料] (\*.xml)。  
  
6. 按一下 [匯出] 。  
  
     每個報告檢視都會儲存到個別的檔案，稱為 \<前置詞>_\<報告檢視名稱>.\<csv&#124;xml>。  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>從 [報告] 檢視視窗匯出效能報告  
  
1. 在 [報告] 檢視視窗中開啟 .vsp 檔案。  
  
2. (選用) 將篩選套用至資料。 如需詳細資訊，請參閱[效能報告檢視篩選](../profiling/performance-report-view-filter.md)。  
  
3. 按一下 [報表] 檢視視窗工具列上的 [匯出報告]  。  
  
4. 選取您想要匯出的報告檢視。  
  
5. 在 [Prefix report with] (在報告前面加入) 下，指定您想要新增至報告名稱的前置詞。  
  
6. 在 [匯出的報告位置] 下，指定目錄。  
  
7. 在 [匯出的報告格式] 下，選取 [逗點分隔] (*.csv) 或 [XML 資料] (\*.xml)。  
  
8. 按一下 [匯出] 。  
  
     每個報告檢視都會儲存到個別的檔案，稱為 \<前置詞>_\<報告檢視名稱>.\<csv&#124;xml>。  
  
## <a name="see-also"></a>請參閱  
 [效能總管](../profiling/performance-explorer.md)   
 [分析效能工具資料](../profiling/analyzing-performance-tools-data.md)   
 [比較效能資料檔案](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)

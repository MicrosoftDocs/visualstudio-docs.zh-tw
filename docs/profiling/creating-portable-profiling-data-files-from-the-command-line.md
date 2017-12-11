---
title: "從命令列建立可移植的分析資料檔案 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f222856d16033cba5ae089c19081efeefe744aa5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>從命令列建立可移植的程式碼剖析資料檔案
若要更輕鬆地共用分析資料，您可以使用 [VSPerfReport](../profiling/vsperfreport.md) 命令列工具，將分析回合的符號內嵌到 .vsp 檔案。  
  
 您也可以建立較小且在 IDE 中更快速載入之預先分析的分析資料 (.vsps) 檔案。  
  
> [!NOTE]
>  請確定 **VSPerfReport** 可以使用符號 (.pdb) 檔案。 如需詳細資訊，請參閱[如何：從命令列指定符號檔位置](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)。  
>   
>  如需 **VSReport** 路徑的資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
>   
>  無法篩選 .vsps 檔案中的分析資料。  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>將分析回合的符號內嵌到分析資料 (.vsp) 檔案  
  
-   在命令提示字元視窗中，鍵入下列命令：  
  
     \<路徑>**VSPerfReport \<**VSP 檔案> **/PackSymbols**  
  
     .vsps 檔案預設會使用 .vsp 檔案的基底名稱進行命名。 您可以使用 **Output** 選項來指定替代名稱。  
  
### <a name="to-create-a-summary-profiling-data-file"></a>建立摘要分析資料檔案  
  
-   在命令提示字元視窗中，鍵入下列命令：  
  
     \<路徑>**VSPerfReport \<**VSP 檔案> **/SummaryFile** [**/Output:**\<檔案名稱>]  
  
     .vsps 檔案預設會使用 .vsp 檔案的基底名稱進行命名。 您可以使用 **Output** 選項來指定替代名稱。
---
title: 從命令列建立可移植的分析資料檔案 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8caa1a4976da39b155edde36d538ca193bd1addd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779489"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>從命令列建立可移植的分析資料檔案
為了簡化分析資料的共用，可以使用[VSPerfReport](../profiling/vsperfreport.md)命令列工具將運行分析的符號嵌入到 中。*vsp*檔。

 您還可以創建預分析的分析資料 （。*vsps*） 檔較小，在 IDE 中載入更快。

> [!NOTE]
> 確保符號 （。*pdb*） 檔可用於**VSPerfReport**。 有關詳細資訊，請參閱[：從命令列指定符號檔位置](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)。
>
> 如需 **VSReport** 路徑的資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。
>
> 中的分析資料。無法篩選*vps*檔。

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>將分析運行的符號嵌入到分析資料 （中。*vsp*） 檔

- 在命令提示字元視窗中，鍵入下列命令：

   \<路徑><strong>VSPerfReport \<</strong>VSP 檔案> **/PackSymbols**

   預設情況下， .*vsps*檔使用 的基名命名。*vsp*檔。 您可以使用 **Output** 選項來指定替代名稱。

### <a name="to-create-a-summary-profiling-data-file"></a>建立摘要分析資料檔案

- 在命令提示字元視窗中，鍵入下列命令：

   \<路徑><strong>VSPerfReport \<</strong>VSP 檔案> **/SummaryFile** [**/Output:**\<檔案名稱>]

   預設情況下， .*vsps*檔使用 的基名命名。*vsp*檔。 您可以使用 **Output** 選項來指定替代名稱。

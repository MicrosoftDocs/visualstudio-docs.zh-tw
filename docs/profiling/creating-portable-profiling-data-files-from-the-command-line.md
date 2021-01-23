---
title: 分析命令列-建立可移植的資料檔案
description: 若要更輕鬆地共用分析資料，請使用 VSPerfReport.exe 命令列工具，將程式碼剖析執行的符號內嵌到 .vsp 檔案中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5df9f14fecce23eb72d08dcba87dee360269e078
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718963"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>從命令列建立可移植的分析資料檔案
若要更輕鬆地共用分析資料，您可以使用 [VSPerfReport](../profiling/vsperfreport.md) 命令列工具，將程式碼剖析執行的符號內嵌至。*.vsp* 檔案。

 您也可以 ( 建立預先分析的分析資料。*.vsps*) 檔案較小，而且可在 IDE 中更快速載入。

> [!NOTE]
> 請確定符號 (。*pdb*) 檔案可供 **VSPerfReport**。 如需詳細資訊，請參閱 [如何：從命令列指定符號檔位置](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)。
>
> 如需 **VSReport** 路徑的資訊，請參閱 [指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。
>
> 中的程式碼剖析資料。無法篩選 *.vsps* 檔案。

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>將程式碼剖析執行的符號內嵌到分析資料 ( 中。*.vsp*) 檔案

- 在命令提示字元視窗中，鍵入下列命令：

   \<Path><strong>VSPerfReport \<</strong> .Vsp File> **/PackSymbols**

   預設為。*.vsps* 檔案的命名方式為的基底名稱。*.vsp* 檔案。 您可以使用 **Output** 選項來指定替代名稱。

### <a name="to-create-a-summary-profiling-data-file"></a>建立摘要分析資料檔案

- 在命令提示字元視窗中，鍵入下列命令：

   \<Path><strong>VSPerfReport \<</strong> .Vsp File> **/SummaryFile** [**/Output：** \<File Name> ]

   預設為。*.vsps* 檔案的命名方式為的基底名稱。*.vsp* 檔案。 您可以使用 **Output** 選項來指定替代名稱。

---
title: 作法：比較效能資料檔案 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ddbf430358dce0ac57dfe5ef36ff8e8861ea0ef8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645299"
---
# <a name="how-to-compare-performance-data-files"></a>作法：比較效能資料檔案
您可以透過建立比較 (「差異」) 報表或檢視，來比較兩個不同的分析工具資料檔案 (.*vsp* 或 .*vsps*) 的結果。 比較會顯示相較於另一個程式碼剖析工作階段所發生的差異、效能衰退和改進。

 差異報告提供資料的資料表檢視。 資料表提供差異或相對於基準的變更。 這是透過判斷舊值、基準值和新分析中的結果值之間的差異計算而來。

 程式碼剖析工具資料的比較可以根據程式碼中的函式、應用程式中的模組、程式行、指令指標 (IP) 及型別。

 設定臨界值可減少雜訊，並以指定的數量篩選掉資料列的資料表檢視中未變更的資料。

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>在效能總管中建立專案的比較檔案檢視

1.  在 [效能總管] 的 [報表] 下方，選取您想要作為比較基準值使用的 .*vsp* 或 .*vsps* 報表檔案。

2.  選取您想要比較的 .*vsp* 或 .*vsps* 報表檔案。

3.  以滑鼠右鍵按一下其中一個選取的檔案，然後按一下 [比較報告]。

### <a name="to-compare-values"></a>比較值

1.  選取 [報告檢視] 視窗中的 [比較報告] 索引標籤 。

2.  在 [資料表] 下拉式清單中，選取要比較的函式或模組。

3.  在 [資料行] 下拉式清單中，選取您要比較的值。

4.  (選擇性) 輸入 [臨界值] 的值。

5.  按一下 [套用]。

### <a name="to-compare-report-files"></a>比較報告檔案

1.  在 [分析] 功能表上，選取 [比較效能報告]。

2.  在 [選取要進行比較的分析檔案] 視窗中，瀏覽並選取 [基準檔案] 分析檔 (.*vsp* 或 .*vsps*) 和 [比較檔案] (.*vsp* 或 .*vsps*)。

3.  按一下 [確定 **Deploying Office Solutions**]。
---
title: 如何：比較效能資料檔案 | Microsoft Docs
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c6dc9d485f6f40eb345ade8f9680be9e0b948106
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778995"
---
# <a name="how-to-compare-performance-data-files"></a>如何：比較效能資料檔案
您可以比較兩個不同的探測器資料檔案的結果 （。*vsp*或 。*vsps*）通過創建比較（"Diff"）報表或視圖。 比較會顯示相較於另一個程式碼剖析工作階段所發生的差異、效能衰退和改進。

 差異報告提供資料的資料表檢視。 表格會呈現相對於基準的差異或變更。 這是透過判斷舊值、基準值和新分析中的結果值之間的差異計算而來。

 程式碼剖析工具資料的比較可以根據程式碼中的函式、應用程式中的模組、程式行、指令指標 (IP) 及型別。

 設定臨界值可減少雜訊，並以指定的數量篩選掉資料列的資料表檢視中未變更的資料。

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>在效能總管中建立專案的比較檔案檢視

1. 在 **"性能資源管理器"** 中，**在"報表"** 下，選擇 。*vsp*或 。*vsps*報告要用作比較基線值的檔。

2. 選擇 。*vsp*或 。*vsps*報告要比較的檔。

3. 以滑鼠右鍵按一下其中一個選取的檔案，然後按一下 [比較報告]****。

### <a name="to-compare-values"></a>比較值

1. 選取 [報告檢視] 視窗中的 [比較報告]**** 索引標籤 。

2. 在 [資料表]**** 下拉式清單中，選取要比較的函式或模組。

3. 在 [資料行]**** 下拉式清單中，選取您要比較的值。

4. (選擇性) 輸入 [臨界值]**** 的值。

5. 按一下 [套用]****。

### <a name="to-compare-report-files"></a>比較報告檔案

1. 在 [分析]**** 功能表上，選取 [比較效能報告]****。

2. 在 **"選擇比較分析檔"** 視窗中，流覽並選擇 **"基線檔**分析檔"（。*vsp*或 。*vsps*）和**比較檔**（.*vsp*或 。*vsps*）。

3. 按一下 [確定]****。

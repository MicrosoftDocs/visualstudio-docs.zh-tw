---
title: 篩選報告檢視 | Microsoft Docs
description: 在 Visual Studio 中，將篩選套用至程式碼剖析資料檔案，以限制顯示于效能報表檢視中的程式碼剖析資料，並將其匯出至報表檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f6ba3e207b180b26ea4b53765926b16fb2e85d48
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801450"
---
# <a name="filter-report-views"></a>篩選報告檢視
您可以在分析資料檔案上套用篩選，限制效能報告檢視中顯示的分析資料，並匯出報表檔案。 您可以將報告限制為介於時間戳記值之間的資料，也可以將資料限制為特定處理序和執行緒。 您可以將篩選儲存到檔案，然後匯入儲存的篩選，在不同的分析資料檔案中建立篩選。

 您也可以在 [摘要] 檢視中使用圖形化時間軸，將報表限制在某個時間區段。 請參閱[如何：從摘要時間表篩選報表檢視](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)。

 若要排除報表中的系統和協力廠商程式碼，請參閱[如何：篩選分析工具報告檢視以顯示 Just My Code](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)

## <a name="procedures"></a>程序

#### <a name="to-create-a-profiler-report-filter"></a>建立分析工具報表篩選

1. 如未顯示 [效能報告檢視篩選條件] 視窗，請按一下效能報表檢視器工具列的 [顯示篩選]。

     效能報告檢視篩選條件是資料表。 資料表的每個資料列都代表篩選的子句。 您可以新增想要篩選的子句，不限數量。

2. 請為想要新增至篩選的每個子句，在資料列的下列欄位中選取或輸入值。

    |欄位|描述|
    |-----------|-----------------|
    |**及/或**|如果這個子句和下一個子句必須同時為 true，請選擇 **和** 以進行結果比對。 如果這個子句或下一個子句可以為 true，請選擇 **或** 以進行結果比對。|
    |**欄位**|從顯示的資料欄位清單中選取要用在篩選子句中的報表欄位。|
    |**運算子**|選取運算子以指定子句的欄位和值之間的關聯性。<br /><br /> =    等於<br /><br /> <>  不等於<br /><br /> <    小於<br /><br /> >    大於<br /><br /> <=  小於或等於<br /><br /> >=  大於或等於|
    |**值**|選取或輸入要尋找的值。 某些欄位會列出可用的欄位值。|

#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>從標記報表檢視建立分析工具報表篩選

1. 從效能報表檢視工具列上的 [目前檢視] 清單中選取 [標記]。

    即顯示標記分析工具報表。

2. 選取要做為報告起點的 ETW 或取樣事件。

3. 按住 CTRL，然後按一下要做為報告結束點使用的事件。

4. 以滑鼠右鍵按一下，再按一下下列選項之一：

   - [在標記上加入篩選條件] 會建立使用 [標記] 資料行做為篩選條件欄位的篩選條件子句。

   - [在時間戳記上加入篩選條件] 會建立使用 [時間戳記 (以毫秒為單位)] 資料行做為篩選條件欄位的篩選條件子句。

     這兩個選項會在相同的起點和終點篩選目前的資料檔案。 如果匯出篩選用於其他報表，任一選項都可能更好。

#### <a name="to-load-an-existing-filter-from-a-file"></a>從檔案載入現有的篩選

1. 在效能報告檢視工具列上，按一下 [匯入篩選]。

     [載入篩選條件] 對話方塊隨即顯示。

2. 指定要載入之篩選條件 (.vspf) 檔案的位置和檔案名稱。

#### <a name="to-execute-a-filter"></a>執行篩選條件

- 在效能報告檢視工具列上，按一下 [執行篩選條件]。

#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>停止花太長時間執行的篩選

- 在效能報告檢視工具列上，按一下 [停止篩選]。

#### <a name="to-remove-a-filter-on-a-report-view"></a>移除報表檢視的篩選

1. 刪除的效能報告檢視篩選條件中的子句資料列。

2. 在效能報告檢視工具列上，按一下 [執行篩選條件]。

#### <a name="to-save-a-filter-to-a-file"></a>將篩選儲存到檔案

1. 在效能報告檢視工具列上，按一下 [匯出篩選]。

     [儲存篩選條件] 對話方塊隨即顯示。

2. 指定要儲存之篩選條件 (.vspf) 檔案的位置和檔案名稱。

## <a name="see-also"></a>另請參閱
- [自訂效能工具報表檢視](../profiling/customizing-performance-tools-report-views.md)

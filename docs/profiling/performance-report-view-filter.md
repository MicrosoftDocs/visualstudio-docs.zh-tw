---
title: 效能報告檢視篩選條件 | Microsoft Docs
description: 瞭解 [分析工具報表檢視篩選] 視窗位於 [效能報表] 視窗頂端的方式。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 79fb4b7cf7a5df4b2077a2145172d24acdbf86cb
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722733"
---
# <a name="performance-report-view-filter"></a>效能報告檢視篩選條件
分析工具 **報表檢視篩選器** 視窗位於 [ **效能報告** ] 視窗的頂端。 如果您看不到這個視窗，請按一下 [顯示篩選條件] 按鈕。

 您可以修改每個篩選條件子句來限定結果。 篩選條件產生器中包含下列資料行。

|篩選條件項目|描述|
|-----------------|-----------------|
|及/或|如果這個子句和下一個子句必須同時為 true，請選擇 **和** 以進行結果比對。 如果這個子句或下一個子句可以為 true，請選擇 **或** 以進行結果比對。|
|欄位|從目前報告檔中可用的資料欄位清單中，選取要在篩選條件子句中使用的欄位。|
|運算子|選擇運算子以指定欄位和值之間的關聯性。<br /><br /> =    等於<br /><br /> <>  不等於<br /><br /> <    小於<br /><br /> >    大於<br /><br /> <=  小於或等於<br /><br /> >=  大於或等於|
|值|選取或輸入要尋找的值。 某些欄位會列出可用的欄位值。|

 您可以加入篩選條件子句，直到您認為篩選條件可以產生最佳結果為止。 按一下 [執行篩選條件]，將篩選條件套用到資料檔案。

 透過 [標記] 報告檢視，您可以產生篩選條件，將報告檢視中的資料限制為在兩個標記之間收集到的資料。 請選取您要做為報告資料開頭和結尾的標記，然後按一下滑鼠右鍵，並選取 [在標記上加入篩選條件] 或 [在時間戳記上加入篩選條件]。 這兩種篩選條件都會將目前資料檔案中的資料限制在相同的範圍內；[在標記上加入篩選條件] 可以套用到其他 .vsp 檔案。

 若要儲存篩選，請按一下 [**效能報表**] 工具列上的 [**匯出篩選**]，然後指定的位置和檔案名。*.vspf* 檔案。 若要載入先前儲存的篩選條件，請按一下 [匯入篩選條件]，並找出已儲存的篩選條件檔案。 您也可以在已安裝獨立程式碼剖析工具的電腦上，使用篩選條件檔案來篩選資料檔案。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。

## <a name="see-also"></a>另請參閱
- [分析效能工具資料](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)

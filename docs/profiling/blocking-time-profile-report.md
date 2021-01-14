---
title: 封鎖時間分析報表 | Microsoft Docs
description: 封鎖時間分析報表提供匯總封鎖時間資料。 有六種報表類型：同步處理、睡眠、i/o、記憶體、搶佔和 UI。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.blocking
helpviewer_keywords:
- Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74cfeb0b93b1819b4491b18b8e455b3c8d49be4d
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204575"
---
# <a name="blocking-time-profile-report"></a>封鎖時間分析報表
分析報表提供每個封鎖類別 (例如 "I/O" 或「同步處理」) 特定之呼叫堆疊的彙總封鎖時間資料 。 先佔報表列出先佔用目前處理序的處理序，以及先佔執行個體的數目。 為建置封鎖分析報表，此工具會收集封鎖的 API 呼叫，並將它們累積成呼叫堆疊的樹狀目錄。 這些報表中所顯示的資料會依據目前的時間範圍、隱藏的執行緒以及下列兩個可套用的篩選而不同︰

- 如果已選取 Just My Code，只會顯示有使用者程式碼的堆疊框架，再加上使用者程式碼下方的一個層級。

- 如果已設定 Noise 減少值，則會略過小於指定頻率的自動分頁堆疊。

  展開任一呼叫樹狀圖項目，以尋找花費封鎖時間的程式碼。 若要尋找某個項目的來源程式行，請在其捷徑功能表上選擇 [檢視原始檔]。 若要尋找呼叫此項目的程式碼，請在捷徑功能表上選擇 [檢視呼叫位置]。 如果只有一個呼叫位置，命令會連線至反白顯示的程式碼 (代表該呼叫位置)。 如果有多個呼叫位置，命令會開啟對話方塊，您可以在其中選取一個項目，再選擇 [移至原始檔] 按鈕來尋找反白顯示的呼叫位置。 檢視有最多執行個體、花費最多時間 (或兩者) 之呼叫位置的原始檔通常最有用。

## <a name="blocking-time-report-columns"></a>封鎖時間報表資料行
 下表顯示每個封鎖時間報表的資料行。

|資料行名稱|描述|
|-----------------|-----------------|
|**名稱**|每個層級的呼叫堆疊的函式名稱。|
|**執行個體**|顯示的時間週期內封鎖呼叫的執行個體數目。|
|**內含封鎖時間**|針對到呼叫堆疊樹狀圖的這個層級為止的所有堆疊花費的總封鎖時間。 此內含數字是此函式的獨佔封鎖時間和其所有子節點的專屬封鎖時間的總和。|
|**獨佔封鎖時間**|花費的總封鎖時間，在此期間內，此函式是呼叫堆疊的最低層級。 具有大量獨佔封鎖時間的唯一呼叫堆疊項目，可能是您感興趣的函式。|
|**API/等候類別**|只針對最下層呼叫堆疊的函式顯示。 已辨識封鎖呼叫的簽章時，會提供封鎖 API 的名稱。 如果無法辨識簽章，會提供核心所報表的資訊。|
|**詳細資料**|函式的完整格式名稱。 當有詳細資料可用時，其中會包括行數。|

### <a name="synchronization"></a>同步處理
 同步處理報表顯示對封鎖同步處理之區段負責的呼叫，以及每個呼叫堆疊的彙總封鎖時間。 如需詳細資訊，請參閱 [同步處理時間](../profiling/synchronization-time.md)。

### <a name="sleep"></a>睡眠
 睡眠報表顯示對因睡眠所花的時間而產生的封鎖時間負責的呼叫，以及每個呼叫堆疊的彙總封鎖時間。 如需詳細資訊，請參閱 [睡眠時間](../profiling/sleep-time.md)。

### <a name="io"></a>I/O
 I/O 報表顯示對封鎖 I/O 之區段負責的呼叫，以及每個呼叫堆疊的彙總封鎖時間。 如需詳細資訊，請參閱 [i/o time (執行緒 view) ](../profiling/i-o-time-threads-view.md)。

### <a name="memory-management"></a>記憶體管理
 記憶體管理報表顯示對封鎖記憶體管理作業之區段負責的呼叫，以及每個呼叫堆疊的彙總封鎖時間。 如需詳細資訊，請參閱 [記憶體管理時間](../profiling/memory-management-time.md)。

### <a name="preemption"></a>先佔
 先佔報表列出先佔用目前處理序的處理序，以及執行個體的數目。  您可以展開各處理序來檢視取代目前處理序中之執行緒的特定執行緒，並檢視每個執行緒先佔執行個體的細目。 此封鎖報表較其他報表不可行，因為先佔通常是由作業系統加諸於您的處理序，而不是由您程式碼中的問題。 如需詳細資訊，請參閱 [搶先時間](../profiling/preemption-time.md)。

### <a name="ui-processing"></a>UI 處理
 UI 處理報表顯示對封鎖 UI 處理區塊之區段負責的呼叫，以及每個呼叫堆疊的彙總封鎖時間。 如需詳細資訊，請參閱 [UI 處理時間](../profiling/ui-processing-time.md)。

## <a name="see-also"></a>請參閱
- [執行緒視圖](../profiling/threads-view-parallel-performance.md)
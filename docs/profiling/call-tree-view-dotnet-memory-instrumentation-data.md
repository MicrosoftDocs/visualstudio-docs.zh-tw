---
title: 呼叫樹狀結構檢視 - .NET 記憶體檢測資料 | Microsoft Docs
description: 閱讀效能總管中 .NET 記憶體配置檢測資料的 [呼叫樹狀檢視]。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: fe6a56101e7fc00d69ed21240fe5a79b298174f2
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150817"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>呼叫樹狀結構檢視 - .NET 記憶體檢測資料
使用檢測方法收集的 .NET 記憶體配置分析資料的 [呼叫樹狀結構] 檢視，會顯示在分析應用程式中周遊的函式執行路徑。 樹狀圖的根是應用程式或元件的進入點。 每個函式節點都會列出它呼叫的所有函式，以及 .NET 記憶體和函式的計時資料。

 [呼叫樹狀圖] 檢視中的值，適用於呼叫樹狀圖中父函式所呼叫的函式執行個體。 百分比值的計算方式是比較函式執行個體值與分析執行中的總配置數目或大小。

## <a name="highlight-the-execution-hot-path"></a>反白顯示執行最忙碌路徑
 [呼叫樹狀結構] 檢視可以展開並反白顯示已建立最大或大部分記憶體物件之處理序或函式的執行路徑。 若要顯示最常使用的路徑，以滑鼠右鍵按一下處理序或函式，然後按一下 [展開最忙碌路徑]。

## <a name="set-the-call-tree-root-node"></a>設定呼叫樹狀圖根節點
 分析執行中的每個處理序都會顯示為根節點。 您可以設定 [呼叫樹狀結構] 檢視的開始節點，方法是以滑鼠右鍵按一下您想要設定為開始節點的節點，然後選取 [設定根目錄]。

 設定根節點時，除了所選取節點的樹狀子目錄以外，請從檢視中排除所有其他的項目。 您可以將根節點重設回所檢視的節點，並以滑鼠右鍵按一下 [呼叫樹狀結構檢視] 視窗，然後選取 [重設根目錄]。

## <a name="general"></a>一般

|Column|描述|
|------------|-----------------|
|**函數名稱**|函式的名稱。|
|**函數位址**|函式的位址。|
|**函式行號**|原始程式檔中這個函式的開頭行號。|
|**呼叫次數**|呼叫此函式的總次數。|
|**來源檔案**|含有這個函式定義的原始程式檔。|
|**模組名稱**|包含該函式的模組名稱。|
|**模組路徑**|包含該函式的模組路徑。|
|**處理序識別碼**|分析執行的處理序 ID (PID)。|
|**進程名稱**|指派給處理序的名稱。|
|**時間專有探查額外負荷**|檢測對這個函式造成的時間額外負荷。 已經從所有專有時間減去探查額外負荷。|
|**時間內含探查額外負荷**|檢測對這個函式及其子函式所造成的時間額外負荷。 已經從所有內含時間減去探查額外負荷。|
|**型別**|函式的內容︰<br /><br /> -   **0** -目前的函式<br />-   **1** -呼叫目前函式的函式<br />-   **2** -目前的函式所呼叫的函式<br /><br /> 只在[VSPerfReport](../profiling/vsperfreport.md) 命令列的報表中。|
|**根函式名稱**|目前函數的名稱。 只在[VSPerfReport](../profiling/vsperfreport.md) 命令列的報表中。|

## <a name="net-memory-values"></a>.NET 記憶體值
 函式的內含 .NET 記憶體值，表示函式及其呼叫的各函式所建立的物件數目 (配置) 和大小 (位元組)。

 專屬記憶體值，表示函式主體中程式碼所建立的物件數量及大小，不是該函式呼叫的各函式所建立的物件數量及大小。

|Column|描述|
|------------|-----------------|
|**內含配置**|此函式執行個體所配置的物件數目，而函式執行個體是由呼叫樹狀結構中的父函式所呼叫。 此數目包含子函式所進行的配置。|
|**內含配置 %**|在分析執行建立的所有物件中，屬於呼叫樹狀結構中父函式所呼叫之函式執行個體的內含配置百分比。|
|**專有配置**|此函式執行個體所配置的物件數目，而函式執行個體是由呼叫樹狀結構中的父函式所呼叫。 此數目未包含子函式所進行的配置。|
|**專有配置 %**|分析回合中建立的所有物件中，屬於呼叫樹狀圖中父函式所呼叫函式執行個體之專有配置的百分比。|

## <a name="elapsed-inclusive-values"></a>功能內含耗用值
 功能內含耗用值表示函式在呼叫堆疊上的時間。 該時間包含函式呼叫函式以及呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。

|Column|描述|
|------------|-----------------|
|**功能內含耗用 (Elapsed Inclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，所有對此函式呼叫的總功能內含耗用 (Elapsed Inclusive) 時間。|
|**功能內含耗用 (Elapsed Inclusive) 時間 %**|在分析執行的總功能內含耗用 (Elapsed Inclusive) 時間中，當呼叫樹狀結構中父函式呼叫此函式時，花費在此函式之總功能內含耗用 (Elapsed Inclusive) 時間的百分比。|
|**平均功能內含耗用 (Elapsed Inclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的平均功能內含耗用 (Elapsed Inclusive) 時間。|
|**最大功能內含耗用 (Elapsed Inclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的最大功能內含耗用 (Elapsed Inclusive) 時間。|
|**最小功能內含耗用 (Elapsed Inclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的最小功能內含耗用 (Elapsed Inclusive) 時間。|

## <a name="elapsed-exclusive-values"></a>功能專屬耗用值
 功能專屬耗用值表示函式直接在呼叫堆疊最上方執行的時間。 該時間包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。 不過，該時間不包括函式呼叫函式所花費的時間。

|Column|描述|
|------------|-----------------|
|**功能專屬耗用 (Elapsed Exclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，所有對此函式呼叫的總功能專屬耗用 (Elapsed Exclusive) 時間。|
|**功能專屬耗用 (Elapsed Exclusive) 時間 %**|在分析執行的總功能專屬耗用 (Elapsed Exclusive) 時間中，當呼叫樹狀結構中父函式呼叫此函式時，花費在此函式之總功能專屬耗用 (Elapsed Exclusive) 時間的百分比。|
|**平均功能專屬耗用 (Elapsed Exclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的平均功能專屬耗用 (Elapsed Exclusive) 時間。|
|**最大功能專屬耗用 (Elapsed Exclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的最大功能專屬耗用 (Elapsed Exclusive) 時間。|
|**最小功能專屬耗用 (Elapsed Exclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的最小功能專屬耗用 (Elapsed Exclusive) 時間。|

## <a name="application-inclusive-values"></a>應用程式內含值
 應用程式內含值表示函式在呼叫堆疊上的時間。 該時間不包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。 該時間確實包括函式呼叫子函式所花費的時間。

|Column|描述|
|------------|-----------------|
|**應用程式內含 (Application Inclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，所有對此函式呼叫的總應用程式內含 (Application Inclusive) 時間。|
|**應用程式內含 (Application Inclusive) 時間 %**|在分析執行的總功能內含耗用 (Elapsed Inclusive) 時間中，當呼叫樹狀結構中父函式呼叫此函式時，花費在此函式之總應用程式內含 (Application Inclusive) 時間的百分比。|
|**平均應用程式內含 (Application Inclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的平均應用程式內含 (Application Inclusive) 時間。|
|**最大應用程式內含 (Application Inclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的最大應用程式內含 (Application Inclusive) 時間。|
|**最小應用程式內含 (Application Inclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的最小應用程式內含 (Application Inclusive) 時間。|

## <a name="application-exclusive-values"></a>應用程式專屬值
 應用程式專屬值，表示在函式中花費的時間，排除在該函式呼叫的子函式中花費的時間。 該時間也排除呼叫作業系統的時間，例如內容切換和輸入/輸出作業。

|Column|描述|
|------------|-----------------|
|**應用程式專屬 (Application Exclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，所有對此函式呼叫的總應用程式專屬 (Application Exclusive) 時間。|
|**應用程式專屬 (Application Exclusive) 時間 %**|在分析執行的總功能專屬耗用 (Elapsed Exclusive) 時間中，當呼叫樹狀結構中父函式呼叫此函式時，花費在此函式之總應用程式專屬 (Application Exclusive) 時間的百分比。|
|**平均應用程式專屬 (Application Exclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的平均應用程式專屬 (Application Exclusive) 時間。|
|**最大應用程式專屬 (Application Exclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的最大應用程式專屬 (Application Exclusive) 時間。|
|**最小應用程式專屬 (Application Exclusive) 時間**|在呼叫樹狀結構中父函式呼叫此函式時，對此函式呼叫的最小應用程式專屬 (Application Exclusive) 時間。|

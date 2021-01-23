---
title: 摘要檢視 - 資源爭用檢視 | Microsoft Docs | Microsoft Docs
description: '[摘要] 檢視顯示因在等候資源存取權而暫停應用程式中執行緒或處理序的事件相關資訊。'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 40d922d8728e53d0098ad67c8b8140f9045c32b0
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722642"
---
# <a name="summary-view---resource-contention-view"></a>摘要檢視 - 資源爭用檢視
[摘要] 檢視顯示因在等候資源存取權而暫停應用程式中執行緒或處理序的事件相關資訊。

 如需包括通知連結和報表清單描述在內的詳細資訊，請參閱[摘要檢視](../profiling/summary-view.md)。

## <a name="timeline-graph"></a>時間軸圖形
 [摘要] 檢視的時間軸圖形會顯示已進行程式碼剖析的應用程式在程式碼剖析期間的爭用事件數目。 您可以使用時間軸圖形，將檢視篩選為選取的時間範圍。 如需詳細資訊，請參閱[如何：從摘要時間軸篩選報表檢視](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)。

## <a name="most-contended-resources"></a>最多爭用的資源
 [最多爭用的資源] 列出應用程式中造成最多爭用事件的資源。 您可以按一下資源名稱來顯示 [爭用] 檢視。 [爭用] 檢視會根據執行緒提供詳細的資源爭用時間軸。

 [最多爭用的資源] 的每個資源都包含下列資料。

|資料行|描述|
|------------|-----------------|
|**名稱**|資源名稱。|
|**爭用 %**|就程式碼剖析資料中的所有爭用事件，爭用此資源所佔的百分比。|

## <a name="most-contended-thread"></a>最多爭用的執行緒
 [最多爭用的執行緒] 列出應用程式中有最多爭用事件數的執行緒。 您可以按一下執行緒名稱，以顯示 [爭用] 檢視，根據執行緒提供詳細的資源爭用時間軸。

 [最多爭用的執行緒] 的每個執行緒都包含下列資料。

|資料行|描述|
|------------|-----------------|
|**識別碼**|執行緒識別碼。|
|**名稱**|擁有該執行緒的處理序名稱。|
|**爭用 %**|就程式碼剖析資料中的所有爭用事件，爭用此資源所佔的百分比。|

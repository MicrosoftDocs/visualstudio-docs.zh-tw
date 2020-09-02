---
title: 摘要檢視 - 資源爭用檢視 | Microsoft Docs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65f659b64b6a1e29e1e25ae344dd8033e631de09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157761"
---
# <a name="summary-view---resource-contention-view"></a>摘要檢視 - 資源爭用檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[摘要] 檢視顯示因在等候資源存取權而暫停應用程式中執行緒或處理序的事件相關資訊。  
  
 如需包括通知連結和報表清單描述在內的詳細資訊，請參閱[摘要檢視](../profiling/summary-view.md)。  
  
## <a name="timeline-graph"></a>時間軸圖形  
 [摘要] 檢視的時間軸圖形會顯示已進行程式碼剖析的應用程式在程式碼剖析期間的爭用事件數目。 您可以使用時間軸圖形，將檢視篩選為選取的時間範圍。 如需詳細資訊，請參閱[如何：從摘要時間軸篩選報表檢視](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)。  
  
## <a name="most-contended-resources"></a>最多爭用的資源  
 [最多爭用的資源]**** 列出應用程式中造成最多爭用事件的資源。 您可以按一下資源名稱來顯示 [爭用] 檢視。 [爭用] 檢視會根據執行緒提供詳細的資源爭用時間軸。  
  
 [最多爭用的資源]**** 的每個資源都包含下列資料。  
  
|資料行|描述|  
|------------|-----------------|  
|**名稱**|資源名稱。|  
|**爭用 %**|就程式碼剖析資料中的所有爭用事件，爭用此資源所佔的百分比。|  
  
## <a name="most-contended-thread"></a>最多爭用的執行緒  
 [最多爭用的執行緒]**** 列出應用程式中有最多爭用事件數的執行緒。 您可以按一下執行緒名稱，以顯示 [爭用] 檢視，根據執行緒提供詳細的資源爭用時間軸。  
  
 [最多爭用的執行緒]**** 的每個執行緒都包含下列資料。  
  
|資料行|描述|  
|------------|-----------------|  
|**識別碼**|執行緒識別碼。|  
|**名稱**|擁有該執行緒的處理序名稱。|  
|**爭用 %**|就程式碼剖析資料中的所有爭用事件，爭用此資源所佔的百分比。|

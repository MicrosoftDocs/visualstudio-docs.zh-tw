---
title: "階層互動檢視 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.tierinteraction
helpviewer_keywords: Tier Interactions view
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9aac5f9ac8886bef61d700209f77b4b1852fe2bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="tier-interactions-view"></a>階層互動檢視
階層互動分析提供透過 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 與資料庫通訊的多介層應用程式函式執行時間的其他資訊。 只針對同步函式呼叫收集資料。  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]  
  
 互動檢視會以兩個窗格顯示階層互動資料︰  
  
-   主要窗格是階層樹狀結構。 最上層資料列包含 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 頁面或處理序資料庫連接的彙總資料。 子節點包含父代資料庫連接的彙總資料。  
  
-   當您按一下主要窗格中的資料庫呼叫節點時，該資料庫呼叫的執行個體資料隨即會顯示在詳細資料窗格中。  
  
 時間會以毫秒數或 CPU 時脈週期數來顯示。 若要變更顯示的時間單位，請按一下 [工具] 功能表，按一下 [選項]，然後選擇其中一項 [時間值顯示為] 選項。  
  
## <a name="master-pane"></a>主要窗格  
  
|Column|描述|  
|------------|-----------------|  
|**Name**|-   對於最上層資料列，其為已進行程式碼剖析的處理序或網頁名稱。<br />-   對於資料庫連接資料列，其為裝載資料庫的伺服器名稱。|  
|**資料庫**|資料庫的名稱 (僅資料庫連接資料列)。|  
|**計數**|處理序、網頁或資料庫連接產生的要求總數。|  
|**總耗用時間**|執行處理序、網頁或資料庫連接的任何一個要求所花費的總時間。|  
|**最大耗用時間**|執行處理序、網頁或資料庫連接的任何一個要求所花費的最大時間。|  
|**最小耗用時間**|執行處理序、網頁或資料庫連接的任何一個要求所花費的最小時間。|  
|**平均耗用時間**|執行處理序、網頁或資料庫連接的要求所花費的平均時間。|  
  
## <a name="database-connection-details-pane"></a>資料庫連接詳細資料窗格  
  
|Column|說明|  
|------------|-----------------|  
|**命令文字**|要求的 SQL 查詢。|  
|**查詢計數**|執行該查詢的次數。|  
|**總耗用時間**|執行該查詢的執行個體所花費的總時間。|  
|**最大耗用時間**|執行該查詢的任何一個執行個體所花費的最大時間。|  
|**最小耗用時間**|執行該查詢的任何一個執行個體所花費的最小時間。|  
|**平均耗用時間**|執行該查詢的執行個體所花費的平均時間。|
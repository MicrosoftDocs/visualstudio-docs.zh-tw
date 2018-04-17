---
title: 一般索引標籤上，處理屬性 對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 54e4eb317b4bd40ce21c4cfcd9a3c1db3948e36f
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="general-tab-process-properties-dialog-box"></a>處理序屬性對話方塊、一般索引標籤
使用**一般**索引標籤，以進一步了解特定的處理程序。 若要顯示[處理序屬性對話方塊](../debugger/process-properties-dialog-box.md)，焦點移至[處理序檢視](../debugger/processes-view.md)視窗。 在樹狀目錄中，選取任何處理序節點，然後選擇 **屬性**從**檢視**功能表。  
  
 下列設定都適用於**一般** 索引標籤：  
  
|進入|描述|  
|-----------|-----------------|  
|**模組名稱**|模組的名稱。|  
|**處理序 ID**|此程序的唯一識別碼。 處理序識別碼為重複使用，因此它們僅針對該程序的存留期可識別程序。 程式執行時，會建立處理程序物件類型。 處理程序中的所有執行緒共用相同的位址空間，並具有相同的資料存取權。|  
|**優先權基底**|此程序目前的基礎優先權。 程序中可以引發並降低他們自己的基礎優先權，相對於處理序的基本優先順序。|  
|**執行緒**|目前使用此程序中的執行緒數目。|  
|**CPU 時間**|在此程序和其執行緒所花費的總 CPU 時間。 等於使用者時間加上特殊權限的時間。|  
|**使用者時間**|累計經過的時間，此程序執行緒所執行的程式碼在使用者模式下非閒置執行緒中。 在使用者模式中的應用程式執行，子系統，例如視窗管理員和圖形引擎一樣。|  
|**特殊權限的時間**|已耗用時間總和此處理序已執行在特權模式下非閒置執行緒中。 服務層、 Executive 常式和核心執行特殊權限模式中。 大部分裝置以外的圖形介面卡和印表機裝置驅動程式也會執行特殊權限模式中。 某些工作的 Windows 應用程式可能會出現在其他子系統處理序，除了特殊權限的時間。|  
|**已耗用時間**|已執行此程序的總時間。|
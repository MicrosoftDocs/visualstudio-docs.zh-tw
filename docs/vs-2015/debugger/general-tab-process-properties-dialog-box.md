---
title: 進程屬性對話方塊、一般索引標籤 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9256ca4141e9e4ec9e5ae218f1e5a11bf2fa5362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182286"
---
# <a name="general-tab-process-properties-dialog-box"></a>處理序屬性對話方塊、一般索引標籤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 [ **一般** ] 索引標籤可深入瞭解特定的進程。 若要顯示 [ [處理常式屬性] 對話方塊](../debugger/process-properties-dialog-box.md)，請將焦點移至 [ [進程] 視圖](../debugger/processes-view.md) 視窗。 選取樹狀結構中的任何進程節點，然後從 [ **View** ] 功能表選擇 [**屬性**]。  
  
 [ **一般** ] 索引標籤提供下列設定：  
  
|進入|描述|  
|-----------|-----------------|  
|**模組名稱**|模組的名稱。|  
|**處理序識別碼**|此進程的唯一識別碼。 處理序識別碼會重複使用，因此它們只會在該進程的存留期內找出處理常式。 當程式執行時，會建立處理常式物件類型。 進程中的所有線程都共用相同的位址空間，而且可以存取相同的資料。|  
|**優先順序基底**|此進程的目前基本優先權。 進程內的執行緒可以提高其本身的基底優先順序（相對於進程的基本優先權）。|  
|**執行緒**|這個處理序目前使用中的執行緒數目。|  
|**CPU 時間**|花費在此進程及其執行緒的總 CPU 時間。 等於使用者時間加上許可權的時間。|  
|**使用者時間**|此進程的執行緒在非閒置執行緒中以使用者模式執行程式碼所經過的累計時間。 應用程式會以使用者模式執行，如同視窗管理員和圖形引擎等子系統。|  
|**授權的時間**|此進程在非閒置執行緒中以特殊許可權模式執行的總經過時間。 服務層級、執行常式和核心會以特殊許可權模式執行。 除了圖形介面卡和印表機之外，大部分裝置的設備磁碟機也會以特殊許可權模式執行。 Windows 針對您的應用程式所做的一些工作，可能會在有許可權的時間之外出現在其他子系統進程中。|  
|**經過時間**|此進程已執行的總經過時間。|

---
title: SccGetEvents 函式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e73fea52d207d4f9834d5c3eabb15bf733c7e23
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488894"
---
# <a name="sccgetevents-function"></a>SccGetEvents 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[SccGetEvents 函式](https://docs.microsoft.com/visualstudio/extensibility/sccgetevents-function)。  
  
此函式會擷取已排入佇列的狀態事件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 lpFileName  
 [in、 out]原始檔控制外掛程式傳回的檔案名稱 （最多 _MAX_PATH 字元為單位） 的放置位置的緩衝區。  
  
 lpStatus  
 [in、 out]會傳回狀態碼 (請參閱[檔案狀態碼](../extensibility/file-status-code-enumerator.md)可能的值)。  
  
 pnEventsRemaining  
 [in、 out]傳回在這個呼叫之後留在佇列的項目數目。 如果這個數字很大，呼叫端可能會決定呼叫[SccQueryInfo](../extensibility/sccqueryinfo-function.md)以取得所有資訊一次。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|取得成功的事件。|  
|SCC_E_OPNOTSUPPORTED|不支援此函式。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 閒置處理，以查看是否有任何狀態更新原始檔控制下的檔案時，會呼叫此函數。 原始檔控制外掛程式會維護狀態的所有檔案，它了解，並每次變更狀態記下外掛程式，狀態和相關聯的檔案會儲存在佇列中。 當`SccGetEvents`呼叫時，頂端佇列項目會擷取並傳回。 此函式會受限於傳回唯一先前快取的資訊，而且必須具有非常快速的作業 （也就是不含磁碟的讀取或詢問原始檔控制系統狀態）;否則可能會開始在 IDE 的效能會降低。  
  
 如果不沒有報告任何狀態更新，原始檔控制外掛程式會將空的字串儲存在所指的緩衝區`lpFileName`。 否則外掛程式儲存檔案的完整路徑名稱的狀態資訊已變更，並傳回適當的狀態碼為 (其中一個值中詳述[檔案狀態碼](../extensibility/file-status-code-enumerator.md))。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)


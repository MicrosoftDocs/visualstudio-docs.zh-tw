---
title: SccGetEvents 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79e517d87acd61eafcd2eb0a12f5a8978912db81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetevents-function"></a>SccGetEvents 函式
此函式會擷取佇列的狀態事件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [in、 out]原始檔控制外掛程式，將傳回的檔名 （最多 _MAX_PATH 字元） 的緩衝區。  
  
 lpStatus  
 [in、 out]會傳回狀態碼 (請參閱[檔案狀態碼](../extensibility/file-status-code-enumerator.md)可能的值)。  
  
 pnEventsRemaining  
 [in、 out]傳回在這個呼叫之後留在佇列的項目數目。 如果這個數字很大，可能會決定呼叫端呼叫[SccQueryInfo](../extensibility/sccqueryinfo-function.md)來取得所有的資訊一次。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|取得成功的事件。|  
|SCC_E_OPNOTSUPPORTED|不支援此函式。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 若要查看是否有任何更新原始檔控制下的檔案的狀態閒置處理時，會呼叫此函數。 原始檔控制外掛程式會維護它所知道的所有檔案的狀態而變更的狀態會記錄下來外掛程式，狀態和相關聯的檔案會儲存在佇列中。 當`SccGetEvents`呼叫時，頁首會擷取佇列的項目，並傳回。 此函式限制為只有先前的快取的資訊傳回，而且必須具有非常快速的作業 （也就是沒有磁碟的讀取或詢問原始檔控制系統的狀態）;否則可能會開始在 IDE 的效能降低。  
  
 如果沒有更新狀態報表，原始檔控制外掛程式會儲存空字串所指向之緩衝區中`lpFileName`。 否則，外掛程式儲存檔案的完整路徑名稱的狀態資訊已變更，並傳回適當的狀態碼為 (其中一個值中詳述[檔案狀態碼](../extensibility/file-status-code-enumerator.md))。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)
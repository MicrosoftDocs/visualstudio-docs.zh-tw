---
title: 檔案狀態碼列舉值 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf7e39f91f6916f4d3ace7a9a303ea1c8e626ee9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954772"
---
# <a name="file-status-code-enumerator"></a>檔案狀態碼列舉值
`SccStatus`列舉值包含具名的常數值會指定在原始檔控制系統中的檔案的狀態。 這個列舉型別由[SccQueryInfo](../extensibility/sccqueryinfo-function.md)並`POPLISTFUNC`回呼函式 (請參閱[POPLISTFUNC](../extensibility/poplistfunc.md)如需詳細資訊)。  
  
## <a name="syntax"></a>語法  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>成員  
 SCC_STATUS_INVALID  
 無法取得狀態;請勿依賴它。  
  
 SCC_STATUS_NOTCONTROLLED  
 檔案不在原始檔控制中。  
  
 SCC_STATUS_CONTROLLED  
 檔案是在原始檔控制。  
  
 SCC_STATUS_CHECKEDOUT  
 簽出目前的使用者，在本機磁碟上。  
  
 SCC_STATUS_OUTOTHER  
 檔案是由其他使用者簽出。  
  
 SCC_STATUS_OUTEXCLUSIVE  
 檔案是以獨佔方式簽出。  
  
 SCC_STATUS_OUTMULTIPLE  
 檔案是由一個以上的使用者簽出。  
  
 SCC_STATUS_OUTOFDATE  
 檔案不是最新的。  
  
 SCC_STATUS_DELETED  
 已從專案刪除檔案。  
  
 SCC_STATUS_LOCKED  
 鎖定檔案;允許任何其他版本。  
  
 SCC_STATUS_MERGED  
 檔案已合併，但尚未修正/驗證。  
  
 SCC_STATUS_SHARED  
 在專案之間共用檔案。  
  
 SCC_STATUS_PINNED  
 明確的版本被共用檔案。  
  
 SCC_STATUS_MODIFIED  
 檔案已修改/中斷/違反。  
  
 SCC_STATUS_OUTBYUSER  
 檔案是由目前的使用者簽出。  
  
 SCC_STATUS_NOMERGE  
 檔案永遠不會與合併，並不需要儲存 GET 之前。  
  
 SCC_STATUS_RESERVED_1  
 保留供內部使用。  
  
 SCC_STATUS_RESERVED_2  
 保留供內部使用。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
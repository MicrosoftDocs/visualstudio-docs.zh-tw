---
title: 檔案狀態碼列舉值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204373"
---
# <a name="file-status-code-enumerator"></a>檔案狀態碼列舉程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SccStatus`列舉值包含指定原始檔控制系統中檔案狀態的指定常數值。 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)和回呼函式會使用這個列舉 `POPLISTFUNC` (如需詳細資料) ，請參閱[POPLISTFUNC](../extensibility/poplistfunc.md) 。  
  
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
 檔案不在原始檔控制之下。  
  
 SCC_STATUS_CONTROLLED  
 檔案在原始檔控制之下。  
  
 SCC_STATUS_CHECKEDOUT  
 由本機磁片上的目前使用者簽出。  
  
 SCC_STATUS_OUTOTHER  
 另一位使用者簽出檔案。  
  
 SCC_STATUS_OUTEXCLUSIVE  
 以獨佔方式簽出檔案。  
  
 SCC_STATUS_OUTMULTIPLE  
 有多個使用者簽出檔案。  
  
 SCC_STATUS_OUTOFDATE  
 檔案不是最新的。  
  
 SCC_STATUS_DELETED  
 已從專案中刪除檔案。  
  
 SCC_STATUS_LOCKED  
 檔案已鎖定;不允許其他版本。  
  
 SCC_STATUS_MERGED  
 檔案已合併，但尚未修正/驗證。  
  
 SCC_STATUS_SHARED  
 檔案會在專案之間共用。  
  
 SCC_STATUS_PINNED  
 檔案會與明確版本共用。  
  
 SCC_STATUS_MODIFIED  
 檔案已遭修改/中斷/違規。  
  
 SCC_STATUS_OUTBYUSER  
 檔案已由目前的使用者簽出。  
  
 SCC_STATUS_NOMERGE  
 檔案永遠不能合併，且不需要在 GET 之前儲存。  
  
 SCC_STATUS_RESERVED_1  
 保留供內部使用。  
  
 SCC_STATUS_RESERVED_2  
 保留供內部使用。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)

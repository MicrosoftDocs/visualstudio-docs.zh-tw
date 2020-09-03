---
title: 目錄狀態碼列舉值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e082a691a389d5cb9a8fa307a627b11911e0db78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185250"
---
# <a name="directory-status-code-enumerator"></a>目錄狀態碼列舉值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SccDirStatus`列舉值包含指定原始檔控制系統中目錄狀態的指定常數值。 此列舉是由 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)所使用。 這是在原始檔控制外掛程式 API 的1.2 版中引進。  
  
## <a name="syntax"></a>語法  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>成員  
 SCC_DIRSTATUS_INVALID  
 無法取得狀態;請勿依賴它。  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 目錄不在原始檔控制之下。  
  
 SCC_DIRSTATUS_CONTROLLED  
 目錄位於原始檔控制之下。  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 對應至此目錄的專案是空的。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)

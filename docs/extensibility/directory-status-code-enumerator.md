---
title: "目錄的狀態碼列舉值 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a29b9453fa7fd36564fef2956c1d41cc7f29cf07
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="directory-status-code-enumerator"></a>目錄的狀態碼列舉值
`SccDirStatus`列舉值包含具名常數的值，指定原始檔控制系統目錄的狀態。 這個列舉型別由[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)。 這是在原始檔控制外掛程式 API 1.2 版中引進。  
  
## <a name="syntax"></a>語法  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>成員  
 SCC_DIRSTATUS_INVALID  
 無法取得狀態。請勿依賴它。  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 目錄不是原始檔控制之下。  
  
 SCC_DIRSTATUS_CONTROLLED  
 目錄是在原始檔控制。  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 專案對應到這個目錄是空的。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
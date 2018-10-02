---
title: 目錄狀態碼列舉值 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24f6dde65def4569eb8163d281f872011be0275c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498643"
---
# <a name="directory-status-code-enumerator"></a>目錄狀態碼列舉值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[目錄狀態碼列舉程式](https://docs.microsoft.com/visualstudio/extensibility/directory-status-code-enumerator)。  
  
`SccDirStatus`列舉值包含具名的常數值會指定在原始檔控制系統中的目錄的狀態。 這個列舉型別由[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)。 這是在原始檔控制外掛程式 API 1.2 版中引進。  
  
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
 無法取得狀態;請勿依賴它。  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 目錄不是原始檔控制之下。  
  
 SCC_DIRSTATUS_CONTROLLED  
 目錄是在原始檔控制。  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 專案對應至這個目錄是空的。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)


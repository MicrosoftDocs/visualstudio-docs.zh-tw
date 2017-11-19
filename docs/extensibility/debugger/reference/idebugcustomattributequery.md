---
title: "IDebugCustomAttributeQuery |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d0c31a25ef2e791eabe4362f27c138ba506d752
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
表示在方法或類型的自訂屬性的查詢。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCustomAttributeQuery : IUnknown  
```  
  
## <a name="methods"></a>方法  
 這個介面會實作下列方法：  
  
|方法|說明|  
|------------|-----------------|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|擷取指定之名稱的自訂屬性。|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|判斷指定的自訂屬性定義。|  
  
## <a name="requirements"></a>需求  
 標頭： Sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll
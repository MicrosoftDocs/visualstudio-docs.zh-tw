---
title: IDebugCustomAttributeQuery |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef26d44f72f762749aff8758d68c7ee2fe765fc3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
表示在方法或類型的自訂屬性的查詢。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCustomAttributeQuery : IUnknown  
```  
  
## <a name="methods"></a>方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|擷取指定之名稱的自訂屬性。|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|判斷指定的自訂屬性定義。|  
  
## <a name="requirements"></a>需求  
 標頭： Sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
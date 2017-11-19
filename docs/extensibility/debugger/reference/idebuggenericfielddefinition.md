---
title: "IDebugGenericFieldDefinition |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e0dd0b65b8b658f58f475e306cac42a118b8423
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
表示欄位的 managed 程式碼的泛型類型定義。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## <a name="methods"></a>方法  
 這個介面會實作下列方法：  
  
|方法|說明|  
|------------|-----------------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|建構指定型別引數陣列的欄位執行個體。|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|擷取指定的參數數目的型別參數。|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|擷取泛型欄位相關聯的型別參數數目。|  
  
## <a name="requirements"></a>需求  
 標頭： Sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll
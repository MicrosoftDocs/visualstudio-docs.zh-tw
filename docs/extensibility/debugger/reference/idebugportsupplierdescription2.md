---
title: IDebugPortSupplierDescription2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c15facb38037272dcf2cef4f06d84d835b874012
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
可讓[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]顯示文字內的 UI**傳輸資訊**區段**附加至處理序** 對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 實作這個介面是由連接埠供應商。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugPortSupplierDescription2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|擷取連接埠供應商的描述和描述中繼資料。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
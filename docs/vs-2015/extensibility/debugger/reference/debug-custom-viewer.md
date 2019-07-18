---
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d10e0811044d7169eaf46f48f53389fa7b3076ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179165"
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

識別自訂檢視器的結構，或輸入視覺化檢視。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```csharp  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>成員  
 dwID  
 識別碼來區別多個檢視器或藉由將其中一個視覺化檢視`GUID`。  
  
 bstrMenuName  
 文字會出現在下拉式選單中。  
  
 bstrDescription  
 自訂檢視器或 （必須是 null 的值如果不使用） 的類型視覺化檢視的描述。  
  
 guidLang  
 提供的運算式評估工具的語言。  
  
 guidVendor  
 提供的運算式評估工具的廠商。  
  
 bstrMetric  
 計量在其下的自訂檢視器或類型視覺化檢視`CLSID`儲存。  
  
## <a name="remarks"></a>備註  
 此結構的清單由呼叫[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法 (和延伸[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

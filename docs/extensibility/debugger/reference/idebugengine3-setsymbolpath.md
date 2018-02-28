---
title: "IDebugEngine3::SetSymbolPath |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8cc60a266a238ee8d3635637b907ce88933b29a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
設定偵錯符號進行搜尋的路徑。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in]字串，包含的符號搜尋路徑。 如需詳細資訊，請參閱 < 備註 >。 不可以是 null。|  
|`szSymbolCachePath`|[in]字串，包含可快取符號的本機路徑。 不可以是 null。|  
|`Flags`|[in]不使用;一律設為 0。|  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 字串`szSymbolSearchPath`是一或多個路徑，以搜尋符號分號分隔的清單。 這些路徑可以是本機路徑、 UNC 樣式路徑或 URL。 這些路徑也可以是不同類型的混合。 如果路徑是 UNC (例如， \\\Symserver\Symbols)，則偵錯引擎應該判斷路徑是否在符號伺服器以及應該要能夠從該伺服器，它們所指定的路徑中的快取中載入符號`szSymbolCachePath`。  
  
 符號路徑也可以包含一或多個快取位置。 快取會依優先順序最高優先順序的快取先列出，並以分隔 * 符號。 例如:   
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)方法會執行實際的符號載入。  
  
## <a name="see-also"></a>請參閱  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
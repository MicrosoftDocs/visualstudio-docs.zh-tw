---
title: IDebugEngine3：： SetSymbolPath |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3ea3086931ab655209a5ca26d4d1527462fb205
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476803"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

設定搜尋以進行偵錯工具符號的路徑或路徑。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
|`szSymbolSearchPath`|在包含符號搜尋路徑或路徑的字串。 如需詳細資訊，請參閱「備註」。 不可為 null。|  
|`szSymbolCachePath`|在字串，其中包含可快取符號的本機路徑。 不可為 null。|  
|`Flags`|在未使用;一律設定為0。|  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 字串 `szSymbolSearchPath` 是一個或多個路徑的清單（以分號分隔），用以搜尋符號。 這些路徑可以是本機路徑、UNC 樣式路徑或 URL。 這些路徑也可以混合不同的類型。 如果路徑是 UNC （例如 \\\Symserver\Symbols），則 debug engine 應該判斷路徑是否為符號伺服器，而且應該能夠從該伺服器載入符號，並在 `szSymbolCachePath`所指定的路徑中進行快取。  
  
 符號路徑也可以包含一或多個快取位置。 快取會依優先順序列出，第一次具有最高優先順序的快取，並以 * 符號分隔。 例如：  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)方法會執行符號的實際載入。  
  
## <a name="see-also"></a>另請參閱  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

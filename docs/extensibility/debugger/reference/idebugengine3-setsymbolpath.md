---
title: "IDebugEngine3::SetSymbolPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetSymbolPath"
helpviewer_keywords: 
  - "IDebugEngine3::SetSymbolPath"
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

設定要進行偵錯符號搜尋的路徑。  
  
## 語法  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```c#  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`szSymbolSearchPath`|\[in\]字串，包含的符號搜尋路徑。  如需詳細資訊，請參閱 「 備註 」。  不可以是 null。|  
|`szSymbolCachePath`|\[in\]字串，包含可快取符號的本機路徑。  不可以是 null。|  
|`Flags`|\[in\]無法使用。 永遠設定為 0。|  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則會傳回錯誤碼。  
  
## 備註  
 字串 `szSymbolSearchPath`是一或多個路徑，以分號隔開，以搜尋符號的清單。  這些路徑可以是本機路徑、 UNC 樣式路徑或 URL。  這些路徑，也可以是不同類型的混合。  如果路徑都是 UNC \(比方說，「 \\\\Symserver\\Symbols 」\)，那麼如果路徑是符號伺服器，應該要能夠從該伺服器，它們中所指定的路徑的快取載入符號，應該決定偵錯引擎`szSymbolCachePath`。  
  
 符號路徑，也可以包含一或多個快取區位置。  快取會依照優先順序最高的優先順序快取中列出的第一次，並且用來分隔 \* 符號。  例如：  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)方法會執行實際載入的符號。  
  
## 請參閱  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
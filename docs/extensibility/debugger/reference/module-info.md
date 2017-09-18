---
title: "MODULE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_INFO"
helpviewer_keywords: 
  - "MODULE_INFO 結構"
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# MODULE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述特定模組 \(DLL、 執行檔或組件\)。  
  
## 語法  
  
```cpp#  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```c#  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## Members  
 dwValidFields  
 從的旗標組合[MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)指定哪些欄位已填寫的列舉型別。  
  
 m\_bstrName  
 模組名稱。  
  
 m\_bstrUrl  
 模組的 URL。  
  
 m\_bstrVersion  
 模組的版本。  
  
 m\_bstrDebugMessage  
 選擇性的訊息相關的模組，比方說，"無法載入符號。"  
  
 m\_addrLoadAddress  
 模組的載入位址。  
  
 m\_addrPreferredLoadAddress  
 模組的慣用的載入位址。  
  
 m\_dwSize  
 模組大小。  
  
 m\_dwLoadOrder  
 模組的載入順序。  
  
 m\_TimeStamp  
 符號檔案上次修改時間。  
  
 m\_bstrUrlSymbolLocation  
 符號檔的位置 \(例如，"。  \\"\) 指定模組中。  若要尋找模組的符號作為起始位置。  
  
 m\_dwModuleFlags  
 從的旗標組合[MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)描述模組的列舉型別。  
  
## 備註  
 這個結構會傳遞至[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)填滿其中的方法。  
  
 這個結構會對應到列在每個模組**模組**視窗。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
---
title: "IntelliSenseHostFlags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IntellisenseHostFlags"
helpviewer_keywords: 
  - "IntelliSense、 IntellisenseHostFlags 列舉型別"
  - "IntellisenseHostFlags 列舉型別"
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定 IntelliSense 主機旗標。  
  
## 語法  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### 參數  
  
|成員|描述|  
|--------|--------|  
|`IHF_READONLYCONTEXT`|內容緩衝區是唯讀的。|  
|`IHF_NOSEPARATESUBJECT`|沒有主體的文字。 內容緩衝區包含 IntelliSense 目標 \(表示 `!IHF_READONLYCONTEXT`\)。|  
|`IHF_SINGLELINESUBJECT`|主旨文字不是多\-列功能。|  
|`IHF_FORCECOMMITTOCONTEXT`|與 `CanCommitIntoReadOnlyBuffer` 相同。|  
|`IHF_OVERTYPE`|編輯 \(在主旨或內容\) 應該在取代模式中執行。|  
  
## 需求  
 SingleFileeditor.idl  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
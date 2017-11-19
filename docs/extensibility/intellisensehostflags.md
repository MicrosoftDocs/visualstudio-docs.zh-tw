---
title: "IntelliSenseHostFlags |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8e00768e544dbd6bb37a4de70e0f730fe967a70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
指定 IntelliSense 主機旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>參數  
  
|成員|說明|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|內容緩衝區是唯讀的。|  
|`IHF_NOSEPARATESUBJECT`|沒有主旨文字。 內容緩衝區包含 IntelliSense 目標 (表示`!IHF_READONLYCONTEXT`)。|  
|`IHF_SINGLELINESUBJECT`|主旨文字不是多-列功能。|  
|`IHF_FORCECOMMITTOCONTEXT`|與 `CanCommitIntoReadOnlyBuffer` 相同。|  
|`IHF_OVERTYPE`|編輯 （在主旨或內容） 應該在取代模式中執行。|  
  
## <a name="requirements"></a>需求  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
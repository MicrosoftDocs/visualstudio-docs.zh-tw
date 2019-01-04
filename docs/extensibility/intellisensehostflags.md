---
title: IntelliSenseHostFlags |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c7482e312dd767a62a18914f496e9b0835f7622b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833228"
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
  
### <a name="parameters"></a>參數  
  
|成員|描述|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|內容緩衝區是唯讀的。|  
|`IHF_NOSEPARATESUBJECT`|沒有主旨文字。 內容緩衝區包含 IntelliSense 目標 (表示`!IHF_READONLYCONTEXT`)。|  
|`IHF_SINGLELINESUBJECT`|無法多-列支援的主旨文字。|  
|`IHF_FORCECOMMITTOCONTEXT`|與 `CanCommitIntoReadOnlyBuffer` 相同。|  
|`IHF_OVERTYPE`|編輯 （在主旨或內容） 應該在取代模式中。|  
  
## <a name="requirements"></a>需求  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
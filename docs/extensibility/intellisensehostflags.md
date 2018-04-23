---
title: IntelliSenseHostFlags |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: a096e79a64168f74150103a5f3ba3a8683fe184e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
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
  
|成員|描述|  
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
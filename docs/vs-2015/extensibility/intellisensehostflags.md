---
title: IntelliSenseHostFlags |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28e78a76c0288cece3c42212a036ff326840b5bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829205"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定 IntelliSense 主機旗標。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
  
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


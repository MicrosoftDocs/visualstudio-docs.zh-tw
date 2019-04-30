---
title: IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::QueryIsChildNode
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 959de620e1e556d92a51dcab0062fa6ff055ec46
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446667"
---
# <a name="idebugapplicationnode100queryischildnode"></a>IDebugApplicationNode100::QueryIsChildNode
判斷指定的文件是否屬於這個節點的子節點的其中一個。  
  
> [!IMPORTANT]
> [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md)是由 PDM v10.0 實作和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT QueryIsChildNode(        [in] IDebugDocument* pSearchKey        );  
```  
  
#### <a name="parameters"></a>參數  
 `pSearchKey`  
 搜尋索引鍵。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md)
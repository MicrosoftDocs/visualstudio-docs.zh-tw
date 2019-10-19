---
title: IDebugApplicationNode100：： GetExcludedDocuments |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::GetExcludedDocuments
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c135aa85ca65a44f6f970e83d7975bb441ff56f5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574762"
---
# <a name="idebugapplicationnode100getexcludeddocuments"></a>IDebugApplicationNode100::GetExcludedDocuments
取得指定的篩選所隱藏的文字檔。  
  
> [!IMPORTANT]
> [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md)是由 PDM 10.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetExcludedDocuments(        [in] APPLICATION_NODE_EVENT_FILTER filter,        [out] TEXT_DOCUMENT_ARRAY* pDocuments        );  
```  
  
#### <a name="parameters"></a>參數  
 `filter`  
 篩選器。  
  
 `pDocuments`  
 一組檔。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md)
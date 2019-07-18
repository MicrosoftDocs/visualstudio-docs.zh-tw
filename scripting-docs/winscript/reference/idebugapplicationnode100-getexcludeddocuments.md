---
title: IDebugApplicationNode100::GetExcludedDocuments |Microsoft Docs
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
ms.openlocfilehash: b8b1793fc1a3aacb27cc612bb5212dc33e7ab7dc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436049"
---
# <a name="idebugapplicationnode100getexcludeddocuments"></a>IDebugApplicationNode100::GetExcludedDocuments
取得指定的篩選條件會隱藏文字文件。  
  
> [!IMPORTANT]
> [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md)是由 PDM v10.0 實作和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetExcludedDocuments(        [in] APPLICATION_NODE_EVENT_FILTER filter,        [out] TEXT_DOCUMENT_ARRAY* pDocuments        );  
```  
  
#### <a name="parameters"></a>參數  
 `filter`  
 篩選器。  
  
 `pDocuments`  
 文件集。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md)
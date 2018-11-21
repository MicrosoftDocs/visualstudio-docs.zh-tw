---
title: IDebugPortSupplier3::CanPersistPorts |Microsoft Docs
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
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c75880fe66e2b8442f1a1027c836557f848d5b7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737801"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會判斷是否連接埠提供者可以保存連接埠 （藉由將它們寫入磁碟） 的偵錯工具的引動過程之間。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="return-value"></a>傳回值  
 `S_OK` 如果可以保存連接埠，或`S_FALSE`表示連接埠，不會保存。  
  
## <a name="remarks"></a>備註  
 如果連接埠提供者可以保存連接埠，它應該這麼做，它會終結時，並再重新載入它們它再次具現化時。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)


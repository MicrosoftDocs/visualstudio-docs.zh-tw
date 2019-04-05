---
title: SccGetVersion 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4e548f1f2b82a97206cdf41174a8c1c7d61e885
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940043"
---
# <a name="sccgetversion-function"></a>SccGetVersion 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式取得支援原始檔控制外掛程式的原始檔控制外掛程式 API 的版本號碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="return-value"></a>傳回值  
 A`LONG`資料類型，包含支援的原始檔控制外掛程式 API 的版本號碼：  
  
|WORD|描述|  
|----------|-----------------|  
|HIWORD|主要版本|  
|取代 LOWORD|次要版本|  
  
## <a name="remarks"></a>備註  
 例如，如果原始檔控制外掛程式支援版本 1.3 的原始檔控制外掛程式 API，此函式會傳回 0x0103。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)

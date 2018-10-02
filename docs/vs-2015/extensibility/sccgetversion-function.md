---
title: SccGetVersion 函式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2b5c5e5e6035d6ce0b81ba747efa3cea65ab2f97
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498589"
---
# <a name="sccgetversion-function"></a>SccGetVersion 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[SccGetVersion 函式](https://docs.microsoft.com/visualstudio/extensibility/sccgetversion-function)。  
  
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


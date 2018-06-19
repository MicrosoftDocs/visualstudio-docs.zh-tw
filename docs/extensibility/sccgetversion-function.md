---
title: SccGetVersion 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70beb89f13d2f752f3adb0f25e2b370fa272171a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136441"
---
# <a name="sccgetversion-function"></a>SccGetVersion 函式
此函式可取得原始檔控制外掛程式 API 支援原始檔控制外掛程式的版本號碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="return-value"></a>傳回值  
 A`LONG`包含支援的原始檔控制外掛程式 API 的版本號碼的資料類型：  
  
|WORD|描述|  
|----------|-----------------|  
|HIWORD|主要版本|  
|取代 LOWORD|次要版本|  
  
## <a name="remarks"></a>備註  
 例如，如果原始檔控制外掛程式支援 1.3 版的原始檔控制外掛程式 API，此函式會傳回 0x0103。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
---
title: StopTrackingAndCleanup | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b6ed74dab67cc2ca718ba312fb657659897c78c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955592"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
停止所有的追蹤，並釋放追蹤工作階段使用的所有記憶體。  
  
## <a name="syntax"></a>語法  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>傳回值  
 如已停止追蹤，則傳回 **HRESULT** 和已設定的 **SUCCEEDED** 位元。  
  
## <a name="requirements"></a>需求  
 **標頭：***FileTracker.h*  
  
## <a name="see-also"></a>另請參閱  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
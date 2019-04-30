---
title: 'Iactivescriptsiteuicontrol:: Getuibehavior 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e3f6247afc70ef1197ea759ffdf475c2d6c0a0c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992225"
---
# <a name="iactivescriptsiteuicontrolgetuibehavior-method"></a>IActiveScriptSiteUIControl::GetUIBehavior 方法
取得[SCRIPTUICHANDLING 列舉](../../winscript/reference/scriptuichandling-enumeration.md)表示應該處理 UI 控制項的方式。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetUIBehavior(     [in] SCRIPTUICITEM UicItem,     [out] SCRIPTUICHANDLING * pUicHandling );   
```  
  
#### <a name="parameters"></a>參數  
 `UicItem`  
 控制項的類型。  
  
 `pUicHandling`  
 應該處理控制項的方式。
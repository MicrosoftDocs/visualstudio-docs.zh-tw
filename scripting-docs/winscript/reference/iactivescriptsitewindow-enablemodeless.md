---
title: IActiveScriptSiteWindow：： EnableModeless |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 756bda6209b6209ff14f6d67fef18faaed0b5618
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574132"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
使主機啟用或停用其主視窗以及任何非強制回應對話方塊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fEnable`  
 在旗標，如果 `TRUE`，則會啟用主視窗和非強制回應對話方塊，或者，如果 `FALSE`，則會停用它們。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`，如果發生錯誤，則傳回 `E_FAIL`。  
  
## <a name="remarks"></a>備註  
 這個方法與 `IOleInPlaceFrame::EnableModeless` 方法相同。  
  
 這個方法的呼叫可以進行嵌套。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)
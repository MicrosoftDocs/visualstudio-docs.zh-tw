---
title: IActiveScriptSiteWindow：： GetWindow |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8263db447c7692ec7b0982127d63b4bea588a4b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574347"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
抓取視窗的控制碼，其可做為腳本引擎必須顯示之快顯視窗的擁有者。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phwnd`  
 脫銷接收視窗控制碼之變數的位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`，如果發生錯誤，則傳回 `E_FAIL`。  
  
## <a name="remarks"></a>備註  
 這個方法類似于 `IOleWindow::GetWindow` 方法。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)
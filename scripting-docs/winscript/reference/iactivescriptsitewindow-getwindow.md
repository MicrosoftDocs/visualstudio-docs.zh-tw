---
title: IActiveScriptSiteWindow::GetWindow |Microsoft Docs
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
ms.openlocfilehash: 7b6efa066765339375a8315695aa9c1de2f9c46b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992083"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
擷取可做為擁有者的指令碼引擎必須顯示快顯視窗的視窗控制代碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phwnd`  
 [out]接收的視窗控制代碼變數位址。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_FAIL`如果發生錯誤。  
  
## <a name="remarks"></a>備註  
 這個方法很類似`IOleWindow::GetWindow`方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)
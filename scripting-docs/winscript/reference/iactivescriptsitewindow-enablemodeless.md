---
title: IActiveScriptSiteWindow::EnableModeless |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4cea23890539ca80abf8e3e58b0f8c48b7ca1fc9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093011"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
會導致主機啟用或停用其主視窗，以及任何非強制回應對話方塊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fEnable`  
 [in]旗標，如果`TRUE`，可讓主視窗和非強制回應對話方塊或，如果`FALSE`，會予以停用。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_FAIL`如果發生錯誤。  
  
## <a name="remarks"></a>備註  
 這個方法相當於`IOleInPlaceFrame::EnableModeless`方法。  
  
 呼叫此方法可以是巢狀。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)
---
title: IActiveScriptSiteWindow |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575902"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
這個介面是由支援與[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)相同物件上之使用者介面的主機所執行。 不支援使用者介面的主機（例如伺服器）不會執行 `IActiveScriptSiteWindow` 介面。 腳本引擎會藉由從 `IActiveScriptSite` 呼叫 `QueryInterface` 來存取此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|抓取視窗控制碼，其可做為腳本引擎必須顯示之快顯視窗的擁有者。|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|使主機啟用或停用其主視窗以及任何非強制回應對話方塊。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)
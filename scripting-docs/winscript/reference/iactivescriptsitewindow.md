---
title: IActiveScriptSiteWindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9a160b17f4a46237ab78b378664a046fe8a0e7d4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345717"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
這個介面實作所支援的使用者介面的相同物件的主機[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 。 不支援使用者介面，例如伺服器、 主機不會實作`IActiveScriptSiteWindow`介面。 指令碼引擎存取這個介面，藉由呼叫`QueryInterface`從`IActiveScriptSite`。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|擷取可做為擁有者的指令碼引擎必須顯示快顯視窗的視窗控制代碼。|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|會導致主機啟用或停用其主視窗，以及任何非強制回應對話方塊。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)
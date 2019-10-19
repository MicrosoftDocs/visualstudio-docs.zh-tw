---
title: IActiveScriptSite |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56b2a749eb3553044bda5816639498a0682e37e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570095"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
由主機所執行，以建立 Windows 腳本引擎的網站。 通常，此網站會與腳本可見之所有物件的容器相關聯（例如 ActiveX 控制項）。 一般而言，此容器會對應至所要查看的檔或頁面。 例如，Microsoft Internet Explorer 會針對每個顯示的 HTML 網頁建立這類容器。 頁面上的每個 ActiveX 控制項（或其他自動化物件）和腳本引擎本身，在此容器中都是可列舉的。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|||  
|-|-|  
|方法|描述|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|抓取主機用來顯示使用者介面元素的地區設定識別碼。|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|透過呼叫[IActiveScript：： AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法，取得已加入至引擎之專案的相關資訊。|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|抓取主機定義的字串，它會從主機的觀點來唯一識別目前的檔版本。|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|當腳本完成執行時呼叫。|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|通知主機腳本引擎已變更狀態。|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|當引擎執行腳本時，通知主機發生執行錯誤。|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|通知主機腳本引擎已開始執行腳本。|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|通知主機腳本引擎已從執行腳本傳回。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)
---
title: IActiveScriptSite | Microsoft Docs
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
ms.openlocfilehash: 67e16e2825f03c9ae452e639d6a086bee584ac95
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152638"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
若要建立 Windows 指令碼引擎的網站主機所實作。 通常，此站台會顯示指令碼 （例如，ActiveX 控制項） 的所有物件的容器相關聯。 一般而言，此容器會對應至文件或頁面檢視。 例如，Microsoft Internet Explorer 中，會建立顯示每個 HTML 網頁這類的容器。 每個 ActiveX 控制項 （或其他自動化物件） 頁面中，與指令碼引擎本身，會列舉此容器中。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|||  
|-|-|  
|方法|描述|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|擷取主機會顯示使用者介面項目使用的地區設定識別碼。|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|取得項目加入至引擎，透過呼叫的相關資訊[iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md)方法。|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|擷取主應用程式定義的字串可唯一識別目前的文件版本，從主機的觀點來看。|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|指令碼完成執行時呼叫。|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|通知主機指令碼引擎已變更狀態。|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|通知主機引擎正在執行指令碼時發生執行錯誤。|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|通知主機，指令碼引擎已開始執行的指令碼。|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|無法執行指令碼程式碼，傳回指令碼引擎通知主機。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)
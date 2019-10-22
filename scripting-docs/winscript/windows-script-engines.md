---
title: Windows 指令碼引擎 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94fca3befc13e32e6e2859c7b1ef6330af7b812f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568951"
---
# <a name="windows-script-engines"></a>Windows 指令碼引擎
若要實作 Microsoft Windows 指令碼引擎，請建立支援下列介面的 OLE COM 物件。  
  
|||  
|-|-|  
|介面|描述|  
|[IActiveScript](../winscript/reference/iactivescript.md)|提供基本的指令碼功能。 需要實作此介面。|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|提供新增指令碼文字、評估運算式等等的能力。 實作此介面是選擇性的，但若不實作它，指令碼引擎就必須實作其中一個 IPersist* 介面才能載入指令碼。|  
|IPersist*|提供持續性支援。 如未實作 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md)，至少需要實作下列一個介面。<br /><br /> IPersistStorage：提供對 OBJECT 標記之 DATA={url} 屬性的支援。<br /><br /> IPersistStreamInit：提供對 `IPersistStorage` 以及 OBJECT 標記的 DATA="string-encoded byte stream" 屬性相同的支援。<br /><br /> IPersistPropertyBag：提供對 OBJECT 標記之 PARAM= 屬性的支援。|  
  
> [!NOTE]
> 透過 `IPersist*` 儲存或還原指令碼狀態時，可能永遠不會呼叫指令碼引擎。 而是在呼叫 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) 建立空白指令碼時使用 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md)，然後以 [IActiveScriptParse::AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) 將程式碼片段新增並連接到事件，以 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) 新增一般程式碼。 然而，指令碼引擎應該完全實作至少一個 `IPersist*` 介面 (最好是 `IPersistStreamInit`)，因為其他的主機應用程式可能會嘗試使用它們。  
  
 以下各節會更詳細地說明實作 Windows 指令碼引擎。  
  
 如需詳細資訊，請參閱 [Windows 指令碼介面參考](../winscript/reference/windows-script-interfaces-reference.md)。  
  
## <a name="registry-standard"></a>登錄標準  
 Windows 指令碼引擎可以使用分類識別碼識別本身。 Windows 指令碼目前定義兩個分類識別碼。  
  
|||  
|-|-|  
|Category|描述|  
|CATID_ActiveScript|指示類別識別碼 (CLSID) 是 Windows 指令碼引擎，其至少支援 [IActiveScript](../winscript/reference/iactivescript.md) 介面和持續性機制 (`IPersistStorage`、`IPersistStreamInit` 或 IPersistPropertyBag 介面)。|  
|CATID_ActiveScriptParse|指示 CLSID 是 Windows 指令碼引擎，至少支援 [IActiveScript](../winscript/reference/iactivescript.md) 和 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 介面。|  
  
 雖然 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 不是真的持續性機制，但它確實支援作用相當於 `IPersist*::InitNew` 的 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) 方法。  
  
## <a name="script-engine-states"></a>指令碼引擎狀態  
 在任何時候，Windows 指令碼引擎都可以是數種狀態之一。  
  
|||  
|-|-|  
|狀況|描述|  
|未初始化|指令碼尚未使用 IPersist* 介面初始化或載入，或未設定 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 介面。 這個狀態的指令碼引擎通常無法使用，直到載入指令碼為止。|  
|初始化|指令碼已使用 `IPersist*` 介面初始化並設定 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 介面，但未連接到主機物件和接收事件。 請注意，此狀態只是表示已完成 `IPersist*::Load`、`IPersist*::InitNew` 或 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) 方法，而且已呼叫 [IActiveScript::SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md) 方法。 引擎在此模式中無法執行程式碼。 引擎透過 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) 方法排入佇列主機傳遞給它的程式碼，並在程式碼轉換至已啟動狀態之後執行。<br /><br /> 因為語言在語意中有極大的差異，所以不要求指令碼引擎支援這項狀態轉換。 但是，支援 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) 方法的引擎必須支援這項狀態轉換。 主機必須做好這項轉換的準備，並採取適當的動作：釋放目前的指令碼引擎、建立新的指令碼引擎，呼叫 `IPersist*::Load`、`IPersist*::InitNew` 或 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) (也可能呼叫 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md))。 使用這項轉換應該視為上述步驟的最佳化。 請注意，指令碼引擎取得之任何具名項目的名稱資訊及描述具名項目的類型資訊，仍然有效。<br /><br /> 因為語言差異極大，定義這項轉換的精確語意很困難。 至少，指令碼引擎必須中斷與所有事件的連接，釋放因呼叫 [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) 方法所取得的所有 SCRIPTINFO_IUNKNOWN 指標。 再次執行指令碼之後，引擎必須重新取得這些指標。 指令碼引擎也應該將指令碼重設為回適合語言的初始狀態。 例如 VBScript，重設所有變數，並保留透過呼叫設有 SCRIPTTEXT_ISPERSISTENT 旗標的 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) 而動態新增的所有程式碼。 其他語言可能需要保留目前的值 (例如 Lisp，因為沒有程式碼/資料區隔)，或重設為已知的狀態 (這包括有以靜態方式初始化變數的語言)。<br /><br /> 請注意，當呼叫 `IPersist*::Save` 儲存指令碼引擎，然後呼叫 `IPersist*::Load` 載入新的指令碼引擎時，轉換至啟動狀態應該有相同的語意 (亦即指令碼引擎應該保持相同的狀態)，這些動作的語意應該和 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) 相同。 目前不支援 `IActiveScript::Clone` 或 `IPersist*` 的指令碼引擎，應該謹慎考量已啟動狀態轉換的行為方式，以便如果以後新增 `IActiveScript::Clone` 或 `IPersist*` 支援，這類轉換不會違反上述條件。<br /><br /> 在轉換到啟動狀態的期間，指令碼引擎在適當解構函式之後會中斷與事件接收的連線，然後在指令碼中執行。 為避免執行這些解構函式，主機可以先將指令碼移到中斷連線狀態，再移至啟動狀態。<br /><br /> 使用 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 取消執行中的指令碼執行緒，不用等候目前的事件，然後完成執行。|  
|啟動|從初始化狀態轉換為啟動狀態，會讓引擎執行排入初始化狀態佇列中的任何程式碼。 引擎在啟動狀態下可以執行程式碼，但未連線到透過 [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) 方法新增的任何事件。 引擎可以透過呼叫取自 [IActiveScript::GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md) 方法的 IDispatch 介面，或呼叫 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)，來執行程式碼。 進一步的背景初始化 (漸進式載入) 可能仍在進行中，而呼叫設定 SCRIPTSTATE_CONNECTED 旗標的 [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) 方法可能會封鎖指令碼，直到完成初始化。|  
|已連接|載入指令碼，並連線主機物件的接收事件。 如果這是從初始化狀態進行的轉換，指令碼引擎應該先透過啟動狀態轉換，執行必要的動作，再進入連線狀態連接到事件。|  
|中斷連接|指令碼已載入並有執行階段狀態，但暫時中斷與主機物件接收事件的連線。 這可以邏輯方式 (略過已接收的事件) 或實際方式 (呼叫適當連接點上的 IConnectionPoint::Unadvise) 完成。 如果這是從初始化狀態進行的轉換，指令碼引擎應該先透過啟動狀態轉換，執行必要的動作，再進入中斷連線狀態。 正在進行中的事件接收會在狀態變更之前完成 (使用 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 取消執行中的指令碼執行緒)。 此狀態從初始化狀態區別出來，這種狀態下的轉換不會造成指令碼重設、不會重設指令碼的執行階段狀態，也不會執行指令碼初始化程序。|  
|關閉|指令碼已關閉。 指令碼引擎不再運作，並傳回大部分方法的錯誤。|  
  
 下圖顯示各種指令碼引擎狀態之間的關聯性，並顯示會導致某個狀態轉換到另一個狀態的方法。  
  
 下圖顯示指令碼引擎在各種狀態轉換期間執行的動作。  
  
## <a name="scripting-engine-threading"></a>指令碼引擎執行緒處理  
 因為 Windows 指令碼引擎可以用在許多環境中，請務必盡可能保留其執行模型的彈性。 例如，伺服器型主機可能需要保留多執行緒的設計，同時又要以有效率的方式使用 Windows 指令碼。 此時，主機不像一般的應用程式會使用執行緒處理，所以不應有執行緒管理的負擔。 Windows 指令碼達到這種平衡，是限制無限制執行緒指令碼引擎可以回撥主機的方式，將主機從此項負擔中釋放出來。  
  
 伺服器上使用的指令碼引擎通常會實作為無限制執行緒的 COM 物件。 這表示，[IActiveScript](../winscript/reference/iactivescript.md) 介面及其相關聯介面上的方法，可以從處理序中的任何執行緒呼叫，不用封送處理。 （可惜的是，這也表示腳本引擎必須實作為同進程伺服器，因為 OLE 目前不支援無限制執行緒物件的進程封送處理）。同步處理是腳本引擎的責任。 對於不能在內部重新進入或非多執行緒語言模型的指令碼引擎，同步處理可以像使用 mutex 序列化存取指令碼引擎一樣簡單。 當然，如 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 的特定方法，不應該以這種方式序列化，以便可以從另一個執行緒終止無法停止的指令碼。  
  
 [IActiveScript](../winscript/reference/iactivescript.md) 通常是無限制執行緒的這個事實，一般意味著 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 介面和主機的物件模型應該也是無限制執行緒。 這會讓主機的實作變得相當困難，特別是當主機使用單一執行緒 Windows 應用程式和其物件模型中單一執行緒或 Apartment-Model ActiveX 控制項的常見案例。 基於這個理由，下列條件約束會放在指令碼引擎使用的 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 上：  
  
 一律在主機執行緒內容中呼叫指令碼網站。 也就是說，指令碼引擎絕不會呼叫指令碼引擎建立的執行緒內容中的指令碼網站，此網站必須位在透過 [IActiveScript](../winscript/reference/iactivescript.md) 及其衍生項目、透過公開的指令碼引擎分派物件、透過 Windows 訊息從主機呼叫呼叫，或從主機物件模型中的事件來源呼叫的指令碼引擎方法內。  
  
 指令碼網站絕不會從簡易執行緒狀態控制項方法的內容中呼叫 (例如，[IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 方法) 或從 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) 方法。  
  
## <a name="see-also"></a>請參閱  
 [Windows 指令碼介面](../winscript/windows-script-interfaces.md)

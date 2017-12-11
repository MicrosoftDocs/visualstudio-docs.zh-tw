---
title: "Windows 指令碼介面 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 200a1ac1bf273e2515e1e17b6f83c2020ff9884d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="windows-script-interfaces"></a>Windows 指令碼的介面
Microsoft Windows 指令碼介面可讓應用程式新增指令碼和 OLE Automation。 依賴 Windows 指令碼的指令碼主機可以使用來自多個來源和廠商的指令碼引擎，來管理元件之間的指令碼。 指令碼本身的實作 (語言、語法、永續性格式、執行模型等等) 保留給指令碼廠商。  
  
 Windows 指令碼文件分成下列各節：  
  
 [Windows Script Host](../winscript/windows-script-hosts.md)  
  
 [Windows 指令碼引擎](../winscript/windows-script-engines.md)  
  
 [動態指令碼偵錯概觀](../winscript/active-script-debugging-overview.md)  
  
 [動態指令碼分析概觀](../winscript/active-script-profiling-overview.md)  
  
 [Windows 指令碼介面參考](../winscript/reference/windows-script-interfaces-reference.md)  
  
## <a name="windows-script-background"></a>Windows 指令碼背景  
 Windows 指令碼介面分成兩個類別：Windows 指令碼主機和 Windows 指令碼引擎。 主機會建立指令碼引擎，並呼叫引擎來執行指令碼。 Windows 指令碼主機的範例包含：  
  
-   Microsoft Internet Explorer  
  
-   網際網路製作工具  
  
-   Shell  
  
 您可以針對任何語言或執行階段環境開發 Windows 指令碼引擎，包含：  
  
-   Microsoft Visual Basic Scripting Edition (VBScript)  
  
-   Perl  
  
-   Lisp  
  
 若要盡可能彈性地實作主機，請提供 Windows 指令碼的 OLE Automation 包裝函式。 不過，使用此包裝函式物件具現化指令碼引擎的主機無法控制執行階段命名空間、持續性模型等等，因此會直接使用 Windows 指令碼。  
  
 Windows 指令碼設計可隔離只有製作環境才需要的介面項目；因此，非製作主機 (例如瀏覽器和檢視器) 和指令碼引擎 (例如，VBScript) 可以維持輕量型。  
  
## <a name="windows-script-basic-architecture"></a>Windows 指令碼基本架構  
 下圖顯示 Windows 指令碼主機與 Windows 指令碼引擎之間的互動。  
  
 下列清單提供主機與引擎之間的互動所需的步驟。  
  
1.  建立專案。 主機會載入專案或文件  (此步驟不是 Windows 指令碼特有的，但基於完整性而包含)。  
  
2.  建立 Windows 指令碼引擎。 主機會呼叫 `CoCreateInstance` 來建立新的 Windows 指令碼引擎，並指定要使用之特定指令碼引擎的類別識別碼 (CLSID)。 例如，Internet Explorer 的 HTML 瀏覽器可透過 HTML \<OBJECT> 標記的 CLSID= 屬性，收到指令碼引擎類別識別碼。  
  
3.  載入指令碼。 如果已持續保存指令碼內容，則主機會呼叫指令碼引擎的 `IPersist*::Load` 方法，以在其中餵入指令碼儲存體、資料流或屬性包。 否則，主機會使用 `IPersist*::InitNew` 或 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) 方法來建立 Null 指令碼。 將指令碼維護為文字的主機，可以使用 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)，以在呼叫 `IActiveScriptParse::InitNew` 之後，將指令碼的文字饋送至指令碼引擎。  
  
4.  新增具名項目。 針對匯入至指令碼引擎命名空間的每個頂層具名項目 (例如頁面和表單)，主機都會呼叫 [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) 方法，以在引擎的命名空間中建立項目。 如果頂層具名項目已經是步驟 3 所載入指令碼之永續性狀態一部分，則這不是必要步驟。 主機不會使用 `IActiveScript::AddNamedItem` 來新增子層次具名項目 (例如 HTML 頁面上的控制項)；而是引擎會使用主機的 `ITypeInfo` 和 `IDispatch` 介面，從頂層項目間接取得子層次項目。  
  
5.  執行指令碼。 在 [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) 方法中設定 SCRIPTSTATE_CONNECTED 旗標，主機即可讓引擎開始執行指令碼。 此呼叫可能會執行任何指令碼引擎建構工作 (包含靜態繫結、連結至事件 (請參閱下面)，以及執行程式碼)，其方式與指令碼 `main()` 函式類似。  
  
6.  取得項目資訊。 指令碼引擎每次需要建立符號與頂層項目的關聯時，都會呼叫 [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) 方法，以傳回所指定項目的相關資訊。  
  
7.  連結事件。 啟動實際指令碼之前，指令碼引擎透過 `IConnectionPoint` 介面，連線至所有相關物件的事件。  
  
8.  叫用屬性和方法。 指令碼執行時，指令碼引擎透過 `IDispatch::Invoke` 或其他標準 OLE 繫結機制，實現具名物件之方法和屬性的參考。  
  
## <a name="windows-script-terms"></a>Windows 指令碼條款  
 此清單包含本文件中所使用之指令碼相關術語的定義。  
  
|詞彙|定義|  
|----------|----------------|  
|程式碼物件|與具名項目 (例如 Visual Basic 中表單後面的模型) 建立關聯的指令碼引擎所建立的執行個體，或與具名項目建立關聯的 C++ 類別。 最好的是，這是 OLE 元件物件模型 (COM) 物件，可支援 OLE Automation，讓主機或其他非指令碼實體可以操作的式碼物件。|  
|具名項目|主機認為指令碼感興趣的 OLE COM 物件 (最好是支援 OLE Automation 的物件)。 範例包含網頁瀏覽器中的 HTML 網頁和瀏覽器，以及 Microsoft Word 中的文件和對話方塊。|  
|指令碼|構成指令碼引擎所執行之程式的資料。 指令碼可以是任何連續可執行資料，包含文字片段、`pcode` 的區塊，甚至是電腦特有可執行位元組碼。 透過其中一個 `IPersist*` 介面或透過 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 介面，主機就會將指令碼載入至指令碼引擎。|  
|指令碼引擎|處理指令碼的 OLE 物件。 指令碼引擎會實作 [IActiveScript](../winscript/reference/iactivescript.md)，並選擇性地實作 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 介面。|  
|指令碼主機|擁有 Windows 指令碼引擎的應用程式或程式。 主機會實作 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)，並選擇性地實作 [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md) 介面。|  
|程式碼片段|透過 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 介面連結至物件之指令碼的一部分。 程式碼片段的彙總集合是指令碼。|  
|指令碼語言|撰寫指令碼的語言 (例如，VBScript) 以及該語言的語意。|  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼的介面](../winscript/windows-script-interfaces.md)
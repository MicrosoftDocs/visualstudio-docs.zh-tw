---
title: "VSCT XML 結構描述參考 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e02d4ad31a4877dd88dca941c06e38f7eeac82f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML 結構描述參考
提供的命令資料表編譯器結構描述項目，允許子元素和屬性每個。  
  
 以 XML 為基礎的命令表 (.vsct) 的設定檔的整合式的開發環境 (IDE) 中定義 VSPackage 提供的命令項目。 這些項目包含功能表項目、 功能表、 工具列和下拉式方塊。  
  
> [!NOTE]
>  前置處理器可以執行 VSCT 編譯器.vsct 檔。 這通常是因為 c + + 前置處理器，您可以定義包含和巨集具有相同的語法是 c + + 檔案中使用。 這個範例會提供在.vsct 檔**新專案**VSPackage 專案建立精靈。  
  
## <a name="optional-elements"></a>選擇性的項目  
 某些 VSCT 項目是選擇性的。 如果`Parent`未指定引數，會隱含 Group_Undefined:0。 如果`Icon`未指定引數，會隱含 guidOfficeIcon:msotcidNoIcon。 攠摝坫定義時，模擬，也就是通常未使用是選擇性的。  
  
 點陣圖項目可能會內嵌在編譯時期藉由指定的位置中的點陣圖帶`href`引數。 點陣圖區域是在合併過程中複製而不是擷取自 DLL 的資源。 當`href`提供引數，則`usedList`引數成為選用項目，並使用視為點陣圖帶中的所有位置。  
  
 使用符號名稱，必須定義所有 GUID 和 ID 的值。 這些名稱可能定義在標頭檔或 VSCT\<符號 > 區段。 符號名稱必須是本機，透過包含\<Include > 項目，或所參考\<Extern > 項目。 標頭檔中指定從匯入的符號名稱\<Extern > 若是簡單模式的項目 #define 符號值。 值可能是另一個符號，只要該符號已定義過。 GUID 定義必須遵循 OLE 或 c + + 格式。 ID 值可能是十進位數字或十六進位的數字 0 的 x 個前面有下列幾行中所示：  
  
-   {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
-   {0x6d484634、 0xe53d、 0x4a2c，{0xad、 0xcb，0x55、 0x14，0x5c、 0x93，0x62，0xc8 建立}}  
  
 可能會使用 XML 註解，但是反覆存取的圖形化使用者介面 (GUI) 工具可能會捨棄它們。 內容\<註解 > 不論格式維護保證項目。  
  
## <a name="schema-hierarchy"></a>結構描述階層架構  
 .Vsct 檔具有下列主要項目。  
  
 [CommandTable 元素](../extensibility/commandtable-element.md)  
  
 [Extern 元素](../extensibility/extern-element.md)  
  
 [Include 元素](../extensibility/include-element.md)  
  
 [Define 元素](../extensibility/define-element.md)  
  
 [Commands 元素](../extensibility/commands-element.md)  
  
 [CommandPlacements 元素](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings 元素](../extensibility/keybindings-element.md)  
  
 [UsedCommands 元素](../extensibility/usedcommands-element.md)  
  
 [Parent 元素](../extensibility/parent-element.md)  
  
 [Icon 元素](../extensibility/icon-element.md)  
  
 [Strings 元素](../extensibility/strings-element.md)  
  
 [Command Flag 元素](../extensibility/command-flag-element.md)  
  
 [Symbols 元素](../extensibility/symbols-element.md)  
  
 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>請參閱  
 [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [在 VSPackage 中路由傳送命令](../extensibility/internals/command-routing-in-vspackages.md)
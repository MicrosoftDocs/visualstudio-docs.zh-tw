---
title: VSCT XML 結構描述參考 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73267319733dd6e31b21a0a47796f9766250bb89
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586830"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML 結構描述參考
提供的命令資料表編譯器結構描述項目，允許的子系項目和屬性每個。  
  
 以 XML 為基礎的命令資料表設定 (.vsct) 檔案的整合式的開發環境 (IDE) 中定義 VSPackage 提供的命令項目。 這些項目包含功能表項目、 功能表、 工具列和下拉式方塊。  
  
> [!NOTE]
>  VSCT 編譯器可以執行前置處理器在.vsct 檔。 因為這通常是 c + + 前置處理器，您可以定義包含，且包含相同的語法是 c + + 檔案中使用巨集。 .vsct 提供這個範例檔案**新的專案**VSPackage 專案建立精靈。  
  
## <a name="optional-elements"></a>選擇性的項目  
 某些 VSCT 項目是選擇性的。 如果`Parent`未指定引數，會隱含 Group_Undefined:0。 如果`Icon`未指定引數，會隱含 guidOfficeIcon:msotcidNoIcon。 攠摝坫定義時，模擬，也就是通常未使用，是選擇性的。  
  
 可能在編譯時期內嵌點陣圖項目，藉由指定的位置中的點陣圖區`href`引數。 點陣圖區是在合併過程中複製而不是擷取自 DLL 的資源。 當`href`提供引數，則`usedList`引數會變成選用項目，並使用視為點陣圖區中的所有位置。  
  
 使用符號名稱，必須定義所有的 GUID 和 ID 值。 可能會定義這些名稱，在標頭檔或 VSCT\<符號 > 區段。 符號名稱必須是本機路徑，包含透過\<Include > 項目，或所參考\<Extern > 項目。 符號名稱從檔案匯入標頭中指定\<Extern > 如果它遵循簡單的模式的項目 #define 符號值。 值可以是另一個符號，只要該符號已定義過。 GUID 定義必須遵循 OLE 或 c + + 格式。 識別碼值可能是十進位數字或會加上 0 x 的十六進位數字，下列幾行中所示：  
  
-   {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
-   {0x6d484634 0xe53d、 0x4a2c，{0xad、 0xcb，0x55、 0x14，0x5c、 0x93，0x62，0xc8 建立}}  
  
 可能會使用 XML 註解，但是反覆存取的圖形化使用者介面 (GUI) 工具可能會捨棄它們。 內容\<註釋 > 項目保證維持不論格式為何。  
  
## <a name="schema-hierarchy"></a>結構描述階層  
 .Vsct 檔案具有下列主要項目。  
  
 [CommandTable 元素](../extensibility/commandtable-element.md)  
  
 [Extern 元素](../extensibility/extern-element.md)  
  
 [包含項目](../extensibility/include-element.md)  
  
 [定義項目](../extensibility/define-element.md)  
  
 [Commands 元素](../extensibility/commands-element.md)  
  
 [CommandPlacements 元素](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings 元素](../extensibility/keybindings-element.md)  
  
 [UsedCommands 元素](../extensibility/usedcommands-element.md)  
  
 [父項目](../extensibility/parent-element.md)  
  
 [Icon 元素](../extensibility/icon-element.md)  
  
 [Strings 元素](../extensibility/strings-element.md)  
  
 [Command Flag 元素](../extensibility/command-flag-element.md)  
  
 [Symbols 元素](../extensibility/symbols-element.md)  
  
 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [在 Vspackage 中路由傳送命令](../extensibility/internals/command-routing-in-vspackages.md)
---
title: .VSCT XML 架構參考 |Microsoft Docs
description: .VSCT XML 架構參考文章會說明命令資料表編譯器架構元素，其中每個專案都有允許的子項目和屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d82cda9c91642b094deea50eda02676f9bb73f3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905224"
---
# <a name="vsct-xml-schema-reference"></a>.VSCT XML 架構參考
提供命令資料表編譯器架構元素的表格，其中每個專案都有允許的子項目和屬性。

 以 XML 為基礎的命令資料表設定 (. .vsct) 檔會定義 VSPackage 提供給整合式開發環境 (IDE) 的命令元素。 這些元素包括功能表項目、功能表、工具列和下拉式方塊。

> [!NOTE]
> .VSCT 編譯器可以在 .vsct 檔案上執行預處理器。 因為這通常是 c + + 預處理器，所以您可以定義與 c + + 檔案中所使用的語法相同的 include 和宏。 .Vsct 檔案中會提供此專案的範例，而 **新的專案** 嚮導會為 VSPackage 專案建立此檔案。

## <a name="optional-elements"></a>選擇性元素
 某些 .VSCT 元素是選擇性的。 如果 `Parent` 未指定引數，Group_Undefined：0將會被隱含。 如果 `Icon` 未指定引數，則會隱含 guidOfficeIcon： msotcidNoIcon。 定義快速鍵時，通常不會使用的模擬是選擇性的。

 點陣圖專案可以在編譯時期內嵌，方法是在引數中指定點陣圖帶的位置 `href` 。 點陣圖區域會在合併期間複製，而不是從 DLL 的資源解壓縮。 當 `href` 提供引數時， `usedList` 引數會變成選擇性，而點陣圖區域中的所有位置都會被視為已使用。

 所有 GUID 和 ID 值都必須使用符號名稱來定義。 這些名稱可以在標頭檔或 .VSCT 區段中定義 \<Symbols> 。 符號名稱必須是本機、透過專案包含 \<Include> ，或是由專案參考 \<Extern> 。 如果符號名稱 \<Extern> 遵循 #define 符號值的簡單模式，則會從元素中指定的標頭檔匯入符號名稱。 此值可能是另一個符號，只要先前已定義該符號。 GUID 定義必須遵循 OLE 或 c + + 格式。 識別碼值可以是十進位數或前面加上0x 的十六進位數位，如下列幾行所示：

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- {0x6d484634，0xe53d，0x4a2c，{0xad，0xcb，0x55，0x14，0x5c，0x93，0x62，0xc8}}

  您可以使用 XML 批註，但 (GUI) 工具的來回行程圖形化使用者介面可能會捨棄這些批註。 \<Annotation>無論格式為何，都一定會維護元素的內容。

## <a name="schema-hierarchy"></a>結構描述階層
 .Vsct 檔案具有下列主要元素。

- [CommandTable 元素](../extensibility/commandtable-element.md)

- [Extern 元素](../extensibility/extern-element.md)

- [Include 元素](../extensibility/include-element.md)

- [Define 元素](../extensibility/define-element.md)

- [命令元素](../extensibility/commands-element.md)

- [CommandPlacements 元素](../extensibility/commandplacements-element.md)

- [VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)

- [Keybindings.json 元素](../extensibility/keybindings-element.md)

- [UsedCommands 元素](../extensibility/usedcommands-element.md)

- [父元素](../extensibility/parent-element.md)

- [Icon 元素](../extensibility/icon-element.md)

- [Strings 元素](../extensibility/strings-element.md)

- [命令旗標元素](../extensibility/command-flag-element.md)

- [符號元素](../extensibility/symbols-element.md)

- [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>另請參閱
- [Vspackage 如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Vspackage 中的命令路由](../extensibility/internals/command-routing-in-vspackages.md)

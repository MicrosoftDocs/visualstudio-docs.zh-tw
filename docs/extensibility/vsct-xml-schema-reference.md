---
title: VSCT XML 架構參考 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697911"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML 架構參考
提供命令表編譯器架構元素的表,每個元素都允許子元素和屬性。

 基於 XML 的指令表配置 (.vsct) 檔案定義 VSPackage 向整合式開發環境 (IDE) 提供的命令元素。 這些元素包括功能表項、功能表、工具列和組合框。

> [!NOTE]
> VSCT 編譯器可以在 .vsct 檔上運行預處理器。 由於這通常是C++預處理器,因此可以定義具有與C++檔相同的語法的包含和宏。 新專案精靈為 VSPackage**專案**建立的 .vsct 檔案中提供了這方面的範例。

## <a name="optional-elements"></a>選擇元素
 某些 VSCT 元素是可選的。 如果未指定`Parent`參數,則Group_Undefined:0將被暗示。 如果未指定`Icon`參數,則暗示為 guidOfficeIcon:msotcidNoIcon。 定義快捷鍵時,通常未使用的仿真是可選的。

 通過在`href`參數中指定位圖條的位置,可以在編譯時嵌入位圖項。 位圖條條在合併期間複製,而不是從 DLL 的資源中提取。 提供`href`參數時,`usedList`參數變為可選,並且考慮使用位圖條中的所有插槽。

 所有 GUID 和 ID 值都必須使用符號名稱來定義。 這些名稱可以在標題檔中或在 VSCT\<符號>部分中定義。 符號名稱必須是本地的,通過\<「包括>元素包含」,或者\<由 Extern> 元素引用。 符號名稱從\<Extern> 元素中指定的標頭檔中導入,如果它遵循#define SYMBOL VALUE 的簡單模式。 只要該符號以前定義,該值可能是另一個符號。 GUID 定義必須遵循 OLE 或C++格式。 ID 值可以是十進位數位或十六進位數字,前面是 0x,如以下行所示:

- [6D484634-E53D-4a2c-ADCB-55145C9362C8]

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 |

  可以使用 XML 註釋,但往返圖形使用者介面 (GUI) 工具可能會放棄它們。 \<無論格式如何,註釋>元素的內容都保證得到維護。

## <a name="schema-hierarchy"></a>結構描述階層
 .vsct 檔具有以下主要元素。

- [指令表元素](../extensibility/commandtable-element.md)

- [外部元素](../extensibility/extern-element.md)

- [包括元素](../extensibility/include-element.md)

- [定義項目](../extensibility/define-element.md)

- [指令元素](../extensibility/commands-element.md)

- [命令放置元素](../extensibility/commandplacements-element.md)

- [可見性限制元素](../extensibility/visibilityconstraints-element.md)

- [鍵繫結元素](../extensibility/keybindings-element.md)

- [已用指令元素](../extensibility/usedcommands-element.md)

- [父元素](../extensibility/parent-element.md)

- [圖示元素](../extensibility/icon-element.md)

- [字串元素](../extensibility/strings-element.md)

- [命令旗標元素](../extensibility/command-flag-element.md)

- [符號元素](../extensibility/symbols-element.md)

- [條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>另請參閱
- [VS 套件如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VS 套件的指令路由](../extensibility/internals/command-routing-in-vspackages.md)

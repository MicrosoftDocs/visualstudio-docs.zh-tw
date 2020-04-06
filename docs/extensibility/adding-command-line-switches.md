---
title: 新增命令列開關 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740173"
---
# <a name="add-command-line-switches"></a>新增命令列交換器
您可以在執行*devenv.exe*時添加應用於 VSPackage 的命令行開關。 用於<xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute>聲明交換機的名稱及其屬性。 在此示例中,MySwitch 開關被添加到名為**AddCommandSwitchPackage**的 VSPackage 子類,該子類沒有參數,並且自動載入 VSPackage。

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 命名參數顯示在以下說明中。

||||
|-|-|-|-|
| 參數 | 描述|
| 引數 | 交換機的參數數。 可以是"*",也可以是參數清單。 |
| 需求負載 | 如果設置為 1,則自動載入 VS 包,否則設置為 0。 |
| 說明字串 | 要用**devenv /?** 顯示的字串的説明字串或資源 ID。 |
| 名稱 | 開關。 |
| 包裝吉德 | 封裝的 GUID。 |

 參數的第一個值通常是 0 或 1。 特殊值"*"可用於指示命令行的整個其餘部分是參數。 這對於使用者必須傳遞調試器命令字串的調試方案非常有用。

 DemandLoad 值`true`為 (1)`false`或 (0)表示應自動載入 VS 包。

 HelpString 值是顯示在**devenv /?** 幫助顯示。 此值應以"#nnn"的形式,其中 nnn 是整數。 資源檔中的字串值應以新的行字元結尾。

 Name 值是交換機的名稱。

 包吉德值是實現此交換機的包的 GUID。 IDE 使用此 GUID 在命令列交換機適用的註冊表中尋找 VSPackage。

## <a name="retrieve-command-line-switches"></a>檢索命令列交換器
 載入包後,可以通過完成以下步驟來檢索命令行開關。

1. 在 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>的`QueryService`實作<xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>中,<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>呼叫以獲取介面。

2. 調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>以檢索用戶輸入的命令行交換機。

   以下代碼展示如何查找使用者是否輸入了 MySwitch 命令列交換機:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 您有責任在每次載入包時檢查命令列交換機。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)
- [建立PkgDef實用程式](../extensibility/internals/createpkgdef-utility.md)
- [.Pkgdef 檔案](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)

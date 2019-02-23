---
title: 加入命令列參數 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 376dcee6f23ec2633efe1b23f77552ebf33341f2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722599"
---
# <a name="add-command-line-switches"></a>新增命令列參數
您可以新增套用至 VSPackage 的命令列參數時*devenv.exe*執行。 使用<xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute>宣告的參數和其屬性的名稱。 在此範例中，加入名為 VSPackage 的子類別 myswitch 之交換器**AddCommandSwitchPackage**搭配任何引數與自動載入 VSPackage。

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 具名的參數會顯示下列描述中。

||||
|-|-|-|-|
| 參數 | 描述|
| 引數 | 參數的引數數目。 可以是 「 * 」，或引數清單。 |
| DemandLoad | 如果這設定為 1，否則設為 0，如果要自動載入 VSPackage。 |
| HelpString | 說明字串或資源識別碼的字串來顯示具有**devenv /？**。 |
| 名稱 | 此參數。 |
| PackageGuid | 封裝的 GUID。 |

 第一個引數的值通常是 0 或 1。 特殊值為 ' *' 可用來表示整個的其餘部分的命令列引數。 這可以是適用於偵錯的案例，其中使用者必須在偵錯工具命令字串中傳遞。

 DemandLoad 值是`true`(1) 或`false`(0) 表示，應該會自動載入 VSPackage。

 HelpString 值會出現在字串的資源識別碼**devenv /？** 說明顯示。 這個值應該是格式 「 #nnn"其中 nnn 是整數。 資源檔中的字串值應在新行字元結尾。

 名稱值是參數的名稱。

 PackageGuid 值是可實作此交換器封裝的 GUID。 IDE 會使用此 GUID 在命令列參數適用於的登錄中尋找的 VSPackage。

## <a name="retrieve-command-line-switches"></a>擷取命令列參數
 當載入封裝時，您可以藉由完成下列步驟來擷取命令列參數。

1. 在您的 VSPackage 中<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>實作中，呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>以取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>介面。

2. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>擷取使用者輸入的命令列參數。

   下列程式碼顯示如何找出是否 myswitch 之命令列參數中所輸入的使用者：

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 您必須負責每次載入封裝時檢查命令列參數。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)
- [CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)
- [.Pkgdef 檔案](/visualstudio/extensibility/shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file)
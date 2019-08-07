---
title: 新增命令列參數 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c44864285f3e5701604379a110292c29d3f9b78
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821526"
---
# <a name="add-command-line-switches"></a>新增命令列參數
當執行*devenv*時, 您可以新增適用于 VSPackage 的命令列參數。 使用<xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute>宣告參數的名稱及其屬性。 在此範例中, 會針對名為**AddCommandSwitchPackage**的 VSPackage 子類別新增 MySwitch 參數, 但不含任何引數, 而且會自動載入 VSPackage。

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 下列說明中會顯示已命名的參數。

||||
|-|-|-|-|
| 參數 | 描述|
| 引數 | 參數的引數數目。 可以是 "*" 或引數清單。 |
| DemandLoad | 如果此設定為 1, 則自動載入 VSPackage, 否則設定為0。 |
| HelpString | 要以**devenv/？** 顯示之字串的說明字串或資源識別碼。 |
| 名稱 | 參數。 |
| PackageGuid | 封裝的 GUID。 |

 引數的第一個值通常是0或1。 ' * ' 的特殊值可以用來表示命令列的全部餘數都是引數。 這對於在使用者必須傳入偵錯工具命令字串的情況下很有説明。

 DemandLoad 值為`true` (1) 或`false` (0) 表示應該自動載入 VSPackage。

 < > Helpstring 值是出現在**devenv/？** 中的字串資源識別碼。 說明顯示。 這個值的格式應該是 "#nnn", 其中 nnn 是整數。 資源檔中的字串值應該以新的行字元結尾。

 [名稱] 值是參數的名稱。

 PackageGuid 值是用來執行此參數之封裝的 GUID。 IDE 會使用這個 GUID, 在登錄中尋找命令列參數所套用的 VSPackage。

## <a name="retrieve-command-line-switches"></a>取出命令列參數
 載入封裝時, 您可以完成下列步驟來取出命令列參數。

1. 在 VSPackage 的<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>執行中<xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> , 呼叫`QueryService`以取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>介面。

2. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>以取得使用者輸入的命令列參數。

   下列程式碼顯示如何找出使用者是否輸入了 MySwitch 命令列參數:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 每次載入套件時, 您都必須負責檢查您的命令列參數。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)
- [CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)
- [..Pkgdef 檔案](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
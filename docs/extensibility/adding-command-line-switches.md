---
title: 加入命令列參數 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: daef07d0b8dd02f6823717b0c0cb5d68d837ccde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098414"
---
# <a name="adding-command-line-switches"></a>加入命令列參數
您可以新增 devenv.exe 執行時，套用至 VSPackage 的命令列參數。 使用<xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute>來宣告參數和其屬性的名稱。 在此範例中，加入名為 VSPackage 的子類別 myswitch 之交換器**AddCommandSwitchPackage**不使用引數與自動載入的 VSPackage。  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 下表顯示具名的參數  
  
 引數  
 參數的引數數目。 可以是"*"，或引數清單。  
  
 DemandLoad  
 如果這設定為 1，否則設為 0，如果要自動載入 VSPackage。  
  
 HelpString  
 說明字串或資源識別碼的字串來顯示具有**devenv /？**。  
  
 名稱  
 此參數。  
  
 PackageGuid  
 封裝的 GUID。  
  
 第一個引數的值通常是 0 或 1。 特殊值為 ' *' 可用於指出整個命令列的其餘部分是引數。 這可用於偵錯狀況下，使用者必須通過偵錯工具命令字串中的位置。  
  
 DemandLoad 值`true`(1) 或`false`(0) 表示應自動載入 VSPackage。  
  
 HelpString 值是字串，會出現在 devenv 資源識別碼 /？說明顯示。 這個值應該是格式 「 #nnn"其中 nnn 為整數。 資源檔中的字串值應在新行字元結尾。  
  
 名稱值是參數的名稱。  
  
 PackageGuid 值是可實作這個參數封裝的 GUID。 IDE 中找不到 VSPackage 的命令列參數適用於的登錄使用此 GUID。  
  
## <a name="retrieving-command-line-switches"></a>擷取命令列參數  
 當載入封裝時，您可以藉由完成下列步驟來擷取命令列參數。  
  
1.  在您的 VSPackage 中<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>實作，請呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>介面。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>擷取使用者輸入的命令列參數。  
  
 下列程式碼顯示如何找出是否由使用者輸入 myswitch 之命令列參數：  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 您必須負責每次載入您的封裝時檢查命令列參數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)   
 [.Pkgdef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
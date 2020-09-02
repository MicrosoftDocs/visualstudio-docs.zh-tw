---
title: 新增命令列參數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562272"
---
# <a name="adding-command-line-switches"></a>新增命令列參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在執行 devenv.exe 時，新增適用于 VSPackage 的命令列參數。 用 <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> 來宣告參數的名稱和其屬性。 在此範例中，會針對名為 **AddCommandSwitchPackage** 的 VSPackage 子類別加入 MySwitch 參數，但不含任何引數，且會自動載入 VSPackage。  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 下表顯示具名引數  
  
 引數  
 切換的引數數目。 可以是 "*" 或引數清單。  
  
 DemandLoad  
 如果此設定為1，則自動載入 VSPackage，否則設定為0。  
  
 HelpString  
 要以 **devenv/？** 顯示之字串的說明字串或資源識別碼。  
  
 Name  
 參數。  
  
 PackageGuid  
 封裝的 GUID。  
  
 引數的第一個值通常是0或1。 您可以使用 ' * ' 的特殊值，表示命令列的整個其餘部分都是引數。 當使用者必須傳入偵錯工具命令字串時，這會很有用。  
  
 DemandLoad 值可能是 `true` (1) 或 `false` (0) 表示應該自動載入 VSPackage。  
  
 HelpString 值是出現在 devenv/？中的字串資源識別碼。說明顯示。 此值的格式應該是 "#nnn"，其中 nnn 是整數。 資源檔中的字串值應該以換行字元結尾。  
  
 名稱值是參數的名稱。  
  
 PackageGuid 值是用來執行此參數之封裝的 GUID。 IDE 會使用此 GUID，在命令列參數套用的登錄中尋找 VSPackage。  
  
## <a name="retrieving-command-line-switches"></a>正在抓取命令列參數  
 載入封裝時，您可以完成下列步驟來取得命令列參數。  
  
1. 在 VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 執行中，呼叫 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> 以取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> 介面。  
  
2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> 以取得使用者所輸入的命令列參數。  
  
   下列程式碼示範如何找出使用者是否已輸入 MySwitch 命令列參數：  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 您必須負責在每次載入封裝時檢查命令列參數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)   
 [.Pkgdef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)

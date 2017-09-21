---
title: "加入命令列參數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新增的命令列參數"
  - "擷取的命令列參數"
  - "IVsAppCommandLine::GetOption 方法"
  - "命令列參數"
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 加入命令列參數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以新增命令列參數的 devenv.exe 執行時，套用到 VSPackage。 使用 <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> 來宣告的參數和它的屬性名稱。 在此範例中，加入名為 VSPackage 的子類別 myswitch 之交換器 **AddCommandSwitchPackage** 與任何引數和自動載入 VSPackage。  
  
```c#  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 下表中顯示的具名的參數  
  
 引數  
 參數的引數數目。 可以是"\*"，或引數清單。  
  
 DemandLoad  
 如果這設定為 1，否則設為 0，會自動載入 VSPackage。  
  
 HelpString  
 說明字串或資源識別碼的字串來顯示具有 **devenv \/?**。  
  
 名稱  
 此參數。  
  
 PackageGuid  
 封裝的 GUID。  
  
 第一個引數的值通常是 0 或 1。 特殊值為 ' \*' 可用來表示整個的其餘部分的命令列引數。 這可用於偵錯狀況下，使用者必須經過偵錯工具命令字串。  
  
 DemandLoad 值 `true` \(1\) 或 `false` \(0\) 表示應自動載入 VSPackage。  
  
 HelpString 值會出現在 devenv 中字串的資源識別碼 \/?顯示 \[說明。 這個值應該是格式"\#nnn"其中 nnn 是整數。 資源檔中的字串值應該結束新行字元。  
  
 名稱值是參數的名稱。  
  
 PackageGuid 值是可實作這個參數封裝的 GUID。 IDE 會使用此 GUID，在命令列參數適用於的登錄中尋找 VSPackage。  
  
## 擷取命令列參數  
 當載入封裝時，您可以藉由完成下列步驟來擷取命令列參數。  
  
1.  在您的 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 實作中，呼叫 `QueryService` 上 <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> 取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> 介面。  
  
2.  呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> 來擷取使用者輸入的命令列參數。  
  
 下列程式碼顯示如何找出是否 myswitch 之命令列參數中所輸入的使用者:  
  
```c#  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine)); int isPresent = 0; string optionValue = ""; cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 您必須負責每次載入封裝時檢查命令列參數。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)   
 [.Pkgdef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
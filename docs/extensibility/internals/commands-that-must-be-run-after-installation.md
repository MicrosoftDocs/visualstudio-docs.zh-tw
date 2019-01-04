---
title: 必須在安裝後執行的命令 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 691cabb67df53faf23c23e2fa3f05f0ca68038a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915545"
---
# <a name="commands-that-must-be-run-after-installation"></a>必須在安裝後執行的命令
如果您部署您的延伸模組，透過 *.msi*檔案中，您必須執行**devenv /setup**為了讓探索您的擴充功能的 Visual Studio 安裝的一部分。  
  
> [!NOTE]
>  本主題資訊適用於尋找*devenv.exe*使用 Visual Studio 2008 和更早版本。 如需如何探索*devenv.exe*使用較新版 Visual Studio 的詳細資訊，請參閱[偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)。  
  
## <a name="find-devenvexe"></a>找到 devenv.exe  
 您可以找出每個版本*devenv.exe*從登錄值[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]撰寫安裝程式，使用 RegLocator 資料表和 AppSearch 資料表來儲存為屬性的登錄值。 如需詳細資訊，請參閱 <<c0> [ 偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)。  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>若要找出從不同版本的 Visual Studio 的 devenv.exe RegLocator 資料表的資料列  
  
|簽章|根目錄|Key|名稱|類型|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch 對應 RegLocator 資料表的資料列的資料表資料列  
  
|屬性|簽章|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 例如，Visual Studio 安裝程式將寫入的登錄值**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath**做為*C:\VS2008\Common7\IDE\devenv.exe*，必須執行安裝程式的可執行檔的完整路徑。  
  
> [!NOTE]
> RegLocator 資料表的型別資料行是 2，因為它不需要指定簽章資料表中的其他版本資訊。  
  
## <a name="run-devenvexe"></a>執行 devenv.exe  
 之後執行安裝程式中的標準動作 AppSearch，AppSearch 資料表中的每一個屬性有值，指向*devenv.exe*對應版本的 Visual Studio 的檔案。 如果任何指定的登錄值不存在，因為未安裝該版本的 Visual Studio — 指定的屬性設定為 null。  
  
 執行自訂動作屬性所指向的可執行檔的 Windows 安裝程式支援輸入 50。 自訂動作應該包含在指令碼執行選項 中， `msidbCustomActionTypeInScript` (1024) 和`msidbCustomActionTypeCommit`(512)，以確保 VSPackage 已整合到之前已成功安裝[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱 < [CustomAction 表格](https://docs.microsoft.com/windows/desktop/msi/customaction-table)並[自訂動作執行中指令碼選項](https://docs.microsoft.com/windows/desktop/msi/custom-action-in-script-execution-options)。  
  
 自訂動作類型 50 的指定屬性，包含可執行檔的來源資料行和目標資料行中的命令列引數的值。  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>若要執行 devenv.exe CustomAction 資料表的資料列  
  
|動作|類型|原始程式檔|目標|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|  
  
 自訂動作必須編寫至 InstallExecuteSequence 資料表，以排程為在安裝期間執行。 使用條件資料行的每個資料列中對應的屬性，以防止若執行自訂動作版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]系統上未安裝。  
  
> [!NOTE]
>  Null 值的屬性評估為`False`時條件中使用。  
  
 針對每個自訂動作 [順序] 欄的值取決於 Windows 安裝程式套件中的其他順序值。 序列值應該是使得*devenv.exe*以執行自訂動作盡可能接近之前 installfinalize 發生標準動作。  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>若要安排 devenv.exe 自訂動作的 InstallExecuteSequence 資料表  
  
|動作|條件|序列|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
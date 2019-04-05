---
title: 必須在安裝後執行的命令 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8448b00085ab7e7a151c935eee4d8a8b1423bd1b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944840"
---
# <a name="commands-that-must-be-run-after-installation"></a>必須在安裝後執行的命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

如果您部署您的延伸模組，透過.msi 檔案，您必須執行`devenv /setup`為了讓探索您的擴充功能的 Visual Studio 安裝的一部分。  
  
> [!NOTE]
>  本主題資訊適用於尋找 DevEnv 使用 Visual Studio 2008 和更早版本。 如需如何探索 DevEnv 與更新版本的 Visual Studio 的詳細資訊，請參閱[偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)。  
  
## <a name="finding-devenvexe"></a>尋找 devenv.exe  
 您可以找出每個版本的 devenv.exe 從登錄值[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]撰寫安裝程式，使用 RegLocator 資料表和 AppSearch 資料表來儲存為屬性的登錄值。 如需詳細資訊，請參閱 <<c0> [ 偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)。  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>若要找出從不同版本的 Visual Studio 的 devenv.exe RegLocator 資料表的資料列  
  
|Signature_|根目錄|Key|名稱|類型|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch 對應 RegLocator 資料表的資料列的資料表資料列  
  
|屬性|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 例如，Visual Studio 安裝程式將寫入的登錄值**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath**做為**C:\VS2008\Common7\IDE\devenv.exe**，必須執行安裝程式的可執行檔的完整路徑。  
  
 **請注意**RegLocator 類型資料行是 2，因為不需要指定簽章資料表中的其他版本資訊。  
  
## <a name="running-devenvexe"></a>執行 devenv.exe  
 執行安裝程式中的標準動作 AppSearch，AppSearch 資料表中的每一個屬性之後對應版本的 Visual Studio 的 devenv.exe 檔案所指向的值。 如果任何指定的登錄值不存在，因為未安裝該版本的 Visual Studio — 指定的屬性設定為 null。  
  
 執行自訂動作屬性所指向的可執行檔的 Windows 安裝程式支援輸入 50。 自訂動作應該包含在指令碼執行選項、 msidbCustomActionTypeInScript (1024) 以及 msidbCustomActionTypeCommit (512)，以確保 VSPackage 已整合到之前已成功安裝[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 如需詳細資訊，請參閱 CustomAction 資料表和自訂動作指令碼中執行的選項。  
  
 自訂動作類型 50 的指定屬性，包含可執行檔的來源資料行和目標資料行中的命令列引數的值。  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>若要執行 devenv.exe CustomAction 資料表的資料列  
  
|動作|類型|原始程式檔|Target|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|  
  
 自訂動作必須編寫至 InstallExecuteSequence 資料表，以排程為在安裝期間執行。 使用條件資料行的每個資料列中對應的屬性，以防止若執行自訂動作版本[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]系統上未安裝。  
  
> [!NOTE]
>  `Null` 屬性評估為`False`時條件中使用。  
  
 針對每個自訂動作 [順序] 欄的值取決於 Windows 安裝程式套件中的其他順序值。 序列值應為使得 devenv.exe 自訂動作以執行盡可能接近之前 installfinalize 發生標準動作。  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>若要安排 devenv.exe 自訂動作的 InstallExecuteSequence 資料表  
  
|動作|條件|序列|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Installer 安裝 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

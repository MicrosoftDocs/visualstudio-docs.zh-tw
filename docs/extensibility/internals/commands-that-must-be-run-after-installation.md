---
title: "必須在安裝後執行的命令 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2ff4b1e572fd1e0c5c500fbd756d01063665bd1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="commands-that-must-be-run-after-installation"></a>必須在安裝後執行的命令
如果您透過.msi 檔案部署您的擴充功能，您必須執行`devenv /setup`做為您安裝 Visual Studio 來探索您的擴充功能的一部分。  
  
> [!NOTE]
>  本主題資訊適用於尋找 DevEnv Visual Studio 2008 及更早版本。 如需如何探索 DevEnv 的 Visual Studio 版本資訊，請參閱[偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)。  
  
## <a name="finding-devenvexe"></a>尋找 devenv.exe  
 您可以找出每個版本從登錄 devenv.exe 值[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]撰寫安裝程式，使用 RegLocator 資料表和 AppSearch 資料表來儲存為屬性的登錄值。 如需詳細資訊，請參閱[偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)。  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>若要找出從不同版本的 Visual Studio 的 devenv.exe RegLocator 資料表資料列  
  
|Signature_|根|Key|名稱|類型|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch 為對應 RegLocator 資料表資料列的的資料表資料列的  
  
|屬性|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 例如，Visual Studio 安裝程式將寫入的登錄值**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath**為**C:\VS2008\Common7\IDE\devenv.exe**，必須執行安裝程式的可執行檔的完整路徑。  
  
 **請注意**RegLocator 類型資料行是 2，因為不需要指定簽章資料表中的其他版本資訊。  
  
## <a name="running-devenvexe"></a>執行 devenv.exe  
 之後執行安裝程式中的標準動作 AppSearch，AppSearch 資料表中的每一個屬性具有對應版本的 Visual Studio 的 devenv.exe 檔案所指向的值。 如果任一個指定的登錄值不存在，因為未安裝該版本的 Visual Studio-指定的屬性設定為 null。  
  
 執行自訂動作屬性所指向的可執行檔的 Windows 安裝程式支援輸入 50。 自訂動作應該包含執行中指令碼選項、 msidbCustomActionTypeInScript (1024) 和 msidbCustomActionTypeCommit (512)，以確保 VSPackage 已整合到之前已成功安裝[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱 CustomAction 資料表和自訂動作指令碼中執行的選項。  
  
 自訂動作的類型 50 指定做為來源資料行和目標資料行中的命令列引數的值包含可執行檔的屬性。  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>若要執行 devenv.exe CustomAction 資料表資料列  
  
|動作|類型|原始程式檔|目標|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|  
  
 必須撰寫自訂動作到 InstallExecuteSequence 資料表來安排在安裝期間執行它們。 使用以防止若該執行自訂動作的條件資料行的每個資料列中對應的屬性版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]系統上未安裝。  
  
> [!NOTE]
>  `Null`屬性評估為`False`時條件中使用。  
  
 每個自訂動作的序列資料行的值取決於 Windows Installer 套件中的其他順序 」 值。 序列值應該是，使得 devenv.exe 自訂動作會以盡可能接近前 InstallFinalize 標準動作。  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>若要排程的 devenv.exe 自訂動作 InstallExecuteSequence 資料表  
  
|動作|條件|序列|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>請參閱  
 [使用 Windows Installer 安裝 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
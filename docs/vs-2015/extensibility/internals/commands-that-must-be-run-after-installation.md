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
ms.openlocfilehash: 158119759f8e90161e1f3b5267be498dfc1c9b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839166"
---
# <a name="commands-that-must-be-run-after-installation"></a>必須在安裝後執行的命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

如果您透過 .msi 檔案部署擴充功能，您必須 `devenv /setup` 在安裝過程中執行，才能讓 Visual Studio 探索您的擴充功能。  
  
> [!NOTE]
> 本主題中的資訊適用于尋找 Visual Studio 2008 及更早版本的 DevEnv。 如需有關如何使用更新版本的 Visual Studio 探索 DevEnv 的詳細資訊，請參閱偵測 [系統需求](../../extensibility/internals/detecting-system-requirements.md)。  
  
## <a name="finding-devenvexe"></a>尋找 devenv.exe  
 您可以從安裝程式所寫入的登錄值，找出每個版本的 devenv.exe [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，並使用 RegLocator 資料表和 AppSearch 資料表將登錄值儲存為屬性。 如需詳細資訊，請參閱偵測 [系統需求](../../extensibility/internals/detecting-system-requirements.md)。  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator 資料表資料列，以找出不同版本 Visual Studio 的 devenv.exe  
  
|Signature_|Root|按鍵|名稱|類型|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch 對應 RegLocator 資料表資料列的資料表資料列  
  
|屬性|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 例如，Visual Studio 安裝程式會將 **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\9.0\setup\vs\environmentpath** 的登錄值寫入為 **C:\VS2008\Common7\IDE\devenv.exe**，也就是安裝程式必須執行的可執行檔完整路徑。  
  
 **注意** 因為 RegLocator 類型資料行是2，所以不需要在簽章資料表中指定其他版本資訊。  
  
## <a name="running-devenvexe"></a>正在執行 devenv.exe  
 在安裝程式中執行 AppSearch 標準動作之後，AppSearch 資料表中的每個屬性都會有一個值指向對應版本 Visual Studio 的 devenv.exe 檔案。 如果有任何指定的登錄值不存在（因為未安裝該版本的 Visual Studio），則指定的屬性會設定為 null。  
  
 Windows Installer 支援執行屬性指向自訂動作類型50的可執行檔。 自訂動作應該包含腳本內執行選項，msidbCustomActionTypeInScript (1024) 和 msidbCustomActionTypeCommit (512) ，以確保 VSPackage 已成功安裝，然後再將其整合到中 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱 CustomAction 資料表和自訂動作的腳本執行選項。  
  
 50類型的自訂動作會指定包含可執行檔的屬性，做為目標資料行中來源資料行和命令列引數的值。  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction 要執行的資料表資料列 devenv.exe  
  
|動作|類型|來源|目標|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|  
  
 自訂動作必須撰寫至 InstallExecuteSequence 資料表中，以排程在安裝期間執行。 如果系統上未安裝該版本的，請在 [條件] 資料行的每個資料列中使用對應的屬性，以防止執行自訂動作 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
> [!NOTE]
> `Null``False`在條件中使用時，屬性會評估為。  
  
 每個自訂動作之 Sequence 資料行的值，取決於您 Windows Installer 套件中的其他序列值。 順序值應為 devenv.exe 自訂動作在 InstallFinalize 標準動作之前盡可能地以接近的方式執行。  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence 資料表，以排程 devenv.exe 自訂動作  
  
|動作|條件|順序|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Installer 安裝 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

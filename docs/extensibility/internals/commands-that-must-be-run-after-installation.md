---
title: 安裝後必須執行的命令 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e85a03c71064687fdfbacf24b7aa59cd2a47f1a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982028"
---
# <a name="commands-that-must-be-run-after-installation"></a>必須在安裝後執行的命令
如果您透過 *.msi*檔案部署擴充功能，您必須在安裝過程中執行**devenv/setup** ，才能讓 Visual Studio 探索您的擴充功能。

> [!NOTE]
> 本主題中的資訊適用于尋找具有 Visual Studio 2008 和更早版本的*devenv。* 如需如何使用較新版本的 Visual Studio 來探索*devenv*的詳細資訊，請參閱偵測[系統需求](../../extensibility/internals/detecting-system-requirements.md)。

## <a name="find-devenvexe"></a>尋找 devenv .exe
 您可以從 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 安裝程式寫入的登錄值找出每個版本的*devenv* ，其方式是使用 RegLocator 資料表和 AppSearch 資料表，將登錄值儲存為屬性。 如需詳細資訊，請參閱偵測[系統需求](../../extensibility/internals/detecting-system-requirements.md)。

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator 資料表資料列，以從不同版本的 Visual Studio 中找出 devenv .exe

|簽章|路徑|機碼|[屬性]|輸入|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>對應 RegLocator 資料表資料列的 AppSearch 資料表資料列

|屬性|簽章|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 例如，Visual Studio 安裝程式會將**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath**的登錄值寫入為*C:\VS2008\Common7\IDE\devenv.exe*，這是可執行檔的完整路徑。安裝程式必須執行。

> [!NOTE]
> 因為 RegLocator 資料表的類型資料行是2，所以不需要在簽章資料表中指定其他版本資訊。

## <a name="run-devenvexe"></a>執行 devenv .exe
 在安裝程式中執行 AppSearch 標準動作之後，AppSearch 資料表中的每個屬性都有一個值，指向對應版本 Visual Studio 的*devenv 檔案。* 如果沒有任何指定的登錄值，因為未安裝該版本的 Visual Studio，則指定的屬性會設定為 null。

 Windows Installer 支援執行可執行檔，屬性會將其指向自訂動作類型50。 自訂動作應包含腳本內執行選項，`msidbCustomActionTypeInScript` （1024）和 `msidbCustomActionTypeCommit` （512），以確保 VSPackage 已成功安裝，然後才將它整合至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱[CustomAction 資料表](/windows/desktop/msi/customaction-table)和[自訂動作的腳本執行選項](/windows/desktop/msi/custom-action-in-script-execution-options)。

 50類型的自訂動作會指定包含可執行檔的屬性，做為目標資料行中來源資料行和命令列引數的值。

### <a name="customaction-table-rows-to-run-devenvexe"></a>要執行 devenv .exe 的 CustomAction 資料表資料列

|動作|輸入|原始程式檔|Target|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 您必須在 InstallExecuteSequence 資料表中撰寫自訂動作，以排程在安裝期間執行。 在 [條件] 資料行的每個資料列中，使用對應的屬性，以防止在系統上安裝該版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 時，執行自訂動作。

> [!NOTE]
> Null 值屬性在條件中使用時，會評估為 `False`。

 每個自訂動作的 [順序] 資料行值，取決於 Windows Installer 封裝中的其他順序值。 順序值應該是在 InstallFinalize 標準動作之前， *devenv*自訂動作的執行盡可能接近。

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>要排程 devenv .exe 自訂動作的 InstallExecuteSequence 資料表

|動作|條件|序列|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>請參閱
- [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
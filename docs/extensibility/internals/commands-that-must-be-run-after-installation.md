---
title: 安裝後必須執行的指令 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77add5afd5d44358f0077a11bb70559a796e74c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709478"
---
# <a name="commands-that-must-be-run-after-installation"></a>安裝後必須執行的指令
如果透過 *.msi*檔案部署擴展,則必須在安裝時運行**devenv /setup,** 以便 Visual Studio 發現擴展。

> [!NOTE]
> 本主題中的資訊適用於在 Visual Studio 2008 和更早版本查找*devenv.exe。* 有關如何使用 Visual Studio 的版本發現*devenv.exe*的資訊,請參閱[檢測系統要求](../../extensibility/internals/detecting-system-requirements.md)。

## <a name="find-devenvexe"></a>尋找 devenv.exe
 您可以使用 RegLocator 表和 AppSearch 表從[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]安裝程式編寫的註冊表值中尋找每個版本的*devenv.exe,* 將註冊表值儲存為屬性。 有關詳細資訊,請參閱[檢測系統要求](../../extensibility/internals/detecting-system-requirements.md)。

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator 表行,用於尋找不同版本的 Visual Studio 的 devenv.exe

|簽章|Root|Key|名稱|類型|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|軟體_微軟_VisualStudio_7.0\設置_VS|環境路徑|2|
|RL_DevenvExe_2003|2|軟體_微軟_視覺工作室\7.1\設置_VS|環境路徑|2|
|RL_DevenvExe_2005|2|軟體_微軟_VisualStudio_8.0\設置_VS|環境路徑|2|
|RL_DevenvExe_2008|2|軟體_微軟_VisualStudio_9.0\設置_VS|環境路徑|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>相應 RegLocator 表列的應用程式搜尋表列

|屬性|簽章|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 例如,Visual Studio 安裝程式將註冊表值**HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio_9.0_安裝程式_VS_環境路徑**寫入*C:_VS2008_Common7_IDE_devenv.exe,* 安裝程式必須運行的可執行檔的完整路徑。

> [!NOTE]
> 由於 RegLocator 表的類型列為 2,因此無需在簽名表中指定其他版本資訊。

## <a name="run-devenvexe"></a>執行 devenv.exe
 在安裝程式中運行 AppSearch 標準操作後,AppSearch 表中的每個屬性都有一個值,指向相應版本的 Visual Studio 的*devenv.exe*檔。 如果不存在任何指定的註冊表值(因為未安裝該版本的 Visual Studio),則指定屬性設置為 null。

 Windows 安裝程式支援運行一個可執行檔,屬性通過自訂操作類型 50 指向該可執行檔。 自定義操作應包括腳本內執行選項`msidbCustomActionTypeInScript`(1024)`msidbCustomActionTypeCommit`和 (512),以確保 VSPackage 已成功安裝,然後再[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]將其集成到 中。 關於詳細資訊,請參閱[自訂操作表](/windows/desktop/msi/customaction-table)與[自訂操作在文稿內執行選項](/windows/desktop/msi/custom-action-in-script-execution-options)。

 類型 50 的自訂操作指定包含可執行檔的屬性作為"目標"欄中的 Source 欄和命令列參數的值。

### <a name="customaction-table-rows-to-run-devenvexe"></a>要執行 devenv.exe 的自訂操作表行

|動作|類型|來源|目標|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/設定|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/設定|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/設定|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/設定|

 必須將自定義操作創作到「安裝執行順序」表中,以安排它們在安裝期間執行。 在「條件」列的每一行中使用相應的屬性,以防止在系統上未安裝該[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]版本的自定義操作。

> [!NOTE]
> 在條件中使用時,將`False`空值屬性計算為

 每個自定義操作的序列列的值取決於 Windows 安裝程式包中的其他序列值。 序列值應使*devenv.exe*自訂操作盡可能接近安裝 Finalize 標準操作之前。

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>安裝執行序列表以安排 devenv.exe 自訂作業

|動作|條件|順序|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>另請參閱
- [使用 Windows 安裝程式安裝 VS 套件](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

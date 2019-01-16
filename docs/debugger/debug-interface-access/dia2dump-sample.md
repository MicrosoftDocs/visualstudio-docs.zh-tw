---
title: Dia2dump 範例 |Microsoft Docs
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93c103387ff2acd7b041fc103bc519e9ac166593
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859642"
---
# <a name="dia2dump-sample"></a>Dia2dump 範例

Dia2dump 範例示範如何使用 Microsoft 偵錯介面存取軟體開發套件 (DIA SDK) 來查詢資訊的 PDB 檔案。

Dia2dump 範例隨附於 Visual Studio，並包含方案和原始程式檔。 從命令列編譯的可執行檔執行。 它可以顯示完整的程式資料庫 (.pdb) 檔案的內容，或您感興趣的各節。

## <a name="install-the-sample"></a>安裝範例

當您選擇安裝範例**使用 c + + 的桌面開發**Visual Studio 安裝程式中的工作負載。 如需如何安裝 Visual Studio 並選擇特定工作負載和個別元件的資訊，請參閱[安裝 Visual Studio](../../install/install-visual-studio.md)。

安裝時，此範例是在您的 Visual Studio 安裝目錄中名為 \DIA SDK\Samples\DIA2Dump 子目錄中。

## <a name="build-the-sample"></a>建置範例

根據預設，安裝目錄是受保護的目錄。 這表示您必須使用提高權限的開發人員命令提示字元或 Visual Studio 執行個體來建立和編輯這個位置中的範例解決方案。 若要簡化組建，我們建議您先將檔案從範例目錄複製到另一個目錄，例如文件 資料夾，資料夾，然後才建置範例。

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>若要建立 Visual Studio 中的 Dia2Dump 範例

1. 在 Visual Studio 中開啟 DIA2Dump.sln 檔案。 如果您沒有方案複製到另一個目錄，您可能會提示重新啟動 Visual Studio，以提高權限。

1. 在 **方案總管 中**，選取 Dia2Dump 專案 （而非方案）。

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](/cpp/ide/working-with-project-properties)。

1. 開啟**組態屬性** > **C/c + +** > **一般**屬性頁。

1. 在 [**其他 Include 目錄**] 屬性中，選擇下拉式清單控制項中，然後選擇**編輯**。

1. 在 **其他 Include 目錄**對話方塊中的，在 編輯 欄位中，輸入`$(VSInstallDir)DIA SDK\include`目錄。 加入此目錄，以確保編譯器可以找到 dia2.h 檔案。 選取 [確定] 儲存您的變更。

1. 選擇**確定**若要將變更儲存至專案屬性。

1. 在 **建置**功能表上，選擇**重建方案**。 根據預設，Visual Studio 會建置此範例中，位於 偵錯之目錄的子目錄方案的偵錯版本。

1. 關閉 Visual Studio。

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>若要建立在命令列 Dia2Dump 範例

1. 在開發人員命令提示字元視窗中，將變更為複製的範例檔案的目錄。 如果您未將範例複製到另一個目錄中，您必須使用提升權限 （系統管理員身分執行） 開發人員命令提示字元視窗。

1. 輸入命令`nmake makefile`建置 dia2dump.exe 的預設偵錯組態。

## <a name="run-the-dia2dump-sample"></a>執行 Dia2Dump 範例

Dia2Dump.exe 依賴 msdia*版本*.dll COM 伺服器，以提供其服務。 在 Visual Studio 2015 和 Visual Studio 2017 中，此版本會為 msdia140.dll。 如果 msdia*版本*.dll COM 伺服器無法初始化，您必須先 dia2dump.exe 可註冊它。 DIA SDK 目錄具有的 bin 子目錄，其中包含 x86 版本的 DLL。 版本架構機器處於 bin\amd64，適用於 x64 和 ARM 版本處於 bin\arm。 若要註冊 dll，請開啟提升權限的開發人員命令提示字元視窗，並切換至包含您電腦的架構版本的目錄。 輸入命令`regsvr32 msdia140.dll`註冊的 COM 伺服器。

### <a name="to-run-the-sample"></a>若要執行範例

1. 開啟命令提示字元，並切換至包含您建置 dia2dump.exe 的目錄。

1. 輸入命令`dia2dump filename`何處*filename*是要檢查的 PDB 檔案的名稱。 如果 PDB 檔案是另一個目錄中，使用做為檔案的完整路徑*filename*。 此命令會列出 PDB 檔案中的所有資料。

1. Dia2Dump 有其他選項 以顯示選取的資訊。 使用`dia2dump -?`命令，列出所有可用的選項。

## <a name="see-also"></a>另請參閱

- [移植、移轉及升級 Visual Studio 專案](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)  

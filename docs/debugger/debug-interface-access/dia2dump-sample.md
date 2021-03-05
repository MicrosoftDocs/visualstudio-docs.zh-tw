---
description: Dia2dump 範例會示範如何使用 Microsoft Debug Interface Access Software 開發工具組 (DIA SDK) 來查詢 PDB 檔案以取得資訊。
title: Dia2dump 範例 |Microsoft 檔
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a94a16d8e9fd60b042ea7113304b6d14c649b6fa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149183"
---
# <a name="dia2dump-sample"></a>Dia2dump 範例

Dia2dump 範例會示範如何使用 Microsoft Debug Interface Access Software 開發工具組 (DIA SDK) 來查詢 PDB 檔案以取得資訊。

Dia2dump 範例會隨 Visual Studio 一起安裝，並包含方案和原始程式檔。 從命令列執行已編譯的可執行檔。 它可以將整個程式資料庫的內容顯示 ( .pdb) 檔案，或只顯示您感興趣的區段。

## <a name="install-the-sample"></a>安裝範例

當您在 Visual Studio 安裝程式中選擇 [ **使用 c + + 的桌面開發** ] 工作負載時，即會安裝此範例。 如需有關如何安裝 Visual Studio 並選擇特定工作負載和個別元件的詳細資訊，請參閱 [安裝 Visual studio](../../install/install-visual-studio.md)。

安裝時，此範例會在您的 Visual Studio 安裝目錄中，位於名為 \DIA 的子目錄中 SDK\Samples\DIA2Dump。

## <a name="build-the-sample"></a>建置範例

根據預設，安裝目錄是受保護的目錄。 這表示您必須使用提升許可權的開發人員命令提示字元或 Visual Studio 實例，才能在此位置建立和編輯範例方案。 若要簡化組建，建議您先將範例目錄中的檔案複製到另一個目錄，例如 [檔] 資料夾中的資料夾，然後建立範例。

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>若要在 Visual Studio 中建立 Dia2Dump 範例

1. 在 Visual Studio 中開啟 DIA2Dump .sln 檔案。 如果您沒有將方案複製到另一個目錄，系統可能會提示您以較高的許可權重新開機 Visual Studio。

1. 在 [ **方案瀏覽器**] 中，選取 [Dia2Dump] 專案， (不是方案) 。

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](/cpp/build/working-with-project-properties)。

1. 開啟 [設定 **屬性**  >  **C/c + +**  >  **一般**] 屬性頁。

1. 在 [ **其他 Include 目錄** ] 屬性中，選擇下拉式清單控制項，然後選擇 [ **編輯**]。

1. 在 [ **其他 Include 目錄** ] 對話方塊的 [編輯] 欄位中，輸入 `$(VSInstallDir)DIA SDK\include` 目錄。 新增此目錄，以保證編譯器可以找到 dia2 .h 檔案。 選取 [確定] 儲存您的變更。

1. 選擇 **[確定]** ，將您的變更儲存至專案屬性。

1. 在 [ **組建** ] 功能表上，選擇 [ **重建方案**]。 根據預設，Visual Studio 會建立範例的偵錯工具版本，其位於方案目錄的 Debug 子目錄中。

1. 關閉 Visual Studio。

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>若要在命令列建立 Dia2Dump 範例

1. 在開發人員命令提示字元視窗中，切換至您複製範例檔案的目錄。 如果您未將範例複製到另一個目錄，則必須使用提升許可權的 (以系統管理員身分執行) 開發人員命令提示字元視窗。

1. 輸入命令 `nmake makefile` 以建立 dia2dump.exe 的預設偵錯工具設定。

## <a name="run-the-dia2dump-sample"></a>執行 Dia2Dump 範例

Dia2Dump.exe 依賴 msdia *版本*.dll COM 伺服器來提供其服務。 從 Visual Studio 2015 開始，版本是 msdia140.dll。 如果 msdia *版本*.dll COM 伺服器尚未初始化，您必須先註冊它，dia2dump.exe 才能運作。 DIA SDK 目錄具有 bin 子目錄，其中包含 x86 版本的 DLL。 X64 架構機器的版本是在 bin\amd64 中，而 ARM 的版本位於 bin\arm。 若要註冊 dll，請開啟提升許可權的開發人員命令提示字元視窗，然後變更為包含您電腦架構版本的目錄。 輸入用 `regsvr32 msdia140.dll` 來註冊 COM 伺服器的命令。

### <a name="to-run-the-sample"></a>執行範例

1. 開啟命令提示字元，並切換至包含您所建立之 dia2dump.exe 的目錄。

1. 輸入命令 `dia2dump filename` ，其中 *filename* 是要檢查的 PDB 檔案名。 如果 PDB 檔案位於另一個目錄中，請使用檔案的完整路徑做為 *檔案名*。 此命令會列出 PDB 檔案中的所有資料。

1. Dia2Dump 具有其他選項，只能顯示選取的資訊。 使用 `dia2dump -?` 命令來列出所有可用的選項。

## <a name="see-also"></a>另請參閱

- [移植、遷移及升級 Visual Studio 專案](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)

---
title: Help Viewer 系統管理員指南
description: 閱讀 Microsoft Help Viewer 系統管理員指南。 從網際網路部署本機說明內容，或在用戶端電腦上部署預先安裝的本機說明內容。
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e52b03b01f53a8064dc6ec691f751c86266af6a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944299"
---
# <a name="help-viewer-administrator-guide"></a>Help Viewer 系統管理員指南

不管使用或不使用網際網路存取，說明檢視器可讓您管理網路環境的本機說明安裝。 本機說明內容會設定為以每台機器為基礎。 根據預設，使用者必須擁有系統管理員權限，以更新其本機說明安裝。

如果您的網路環境允許用戶端存取網際網路，您可以使用 **Help Content Manager** 可執行檔從網際網路部署本機說明內容。 如需有關 *HlpCtntMgr.exe* 命令列語法的詳細資訊，請參閱 [Help Content Manager 的命令列引數](../help-viewer/command-line-arguments.md)。

如需建立內容、建立內部網路服務端點以及類似活動類型的資訊，請參閱 [Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md)。

如果您的網路環境無法存取網際網路，Help Viewer 可以從內部網路或網路共用部署本機說明內容。 您也可以使用[登錄機碼覆寫](../help-viewer/behavior-overrides.md)，針對下列功能停用 [Visual Studio IDE 說明] 選項：

- 線上與離線說明

- 第一次啟動 IDE 時的內容安裝

- 指定內部網路內容服務

- 管理內容

## <a name="deploy-local-help-content-from-the-internet"></a>從網際網路部署本機說明內容

您可以使用 **Help Content Manager** (*HlpCtntMgr.exe*)，從網際網路將本機說明內容部署至用戶端電腦。 使用下列語法：

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

如需有關 *HlpCtntMgr.exe* 命令列語法的詳細資訊，請參閱 [Help Content Manager 的命令列引數](../help-viewer/command-line-arguments.md)。

需求：

- 用戶端電腦必須能夠存取網際網路。

- 在安裝本機說明內容後，使用者必須擁有系統管理員權限，以更新、新增或移除本機說明內容。

警告：

- 說明的預設來源仍處於線上。

### <a name="example"></a>範例

以下範例將安裝 Visual Studio 的英文內容到用戶端電腦。

#### <a name="to-install-english-content-from-the-internet"></a>從網際網路安裝英文內容

1. 選擇 [開始]，然後選擇 [執行]。

2. 輸入下列命令：

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3. 按 **Enter**。

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>在用戶端電腦上部署預先安裝的本機說明內容

您可以從線上安裝一組內容到一部電腦上，並接著將該組已安裝的內容複製到其他電腦。

需求：

- 您安裝該組內容的電腦必須能夠存取網際網路。

- 在安裝本機說明內容後，使用者必須擁有系統管理員權限，以更新、新增或移除本機說明內容。

    > [!TIP]
    > 如果使用者沒有系統管理員權限，建議您停用 Help Viewer 中的 [管理內容] 索引標籤。 如需詳細資訊，請參閱 [Help Content Manager 覆寫](../help-viewer/behavior-overrides.md)。

警告：

- 說明的預設來源仍處於線上。

### <a name="create-the-content-set"></a>建立內容集

在您可以建立基底內容集之前，您必須先解除安裝目標電腦上的所有本機 Visual Studio 內容。

#### <a name="to-uninstall-local-help"></a>解除安裝本機說明

1. 在 Help Viewer 中，選擇 [管理內容] 索引標籤。

2. 巡覽至 Visual Studio 文件集。

3. 選擇每個子項目旁的 [移除]。

4. 選擇 [更新] 以解除安裝。

5. 流覽至 *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* ，並確認資料夾僅包含 *catalogType.xml* 的檔案。

   一旦移除了所有先前安裝的本機 Visual Studio 說明內容，您已準備好下載基底內容集。

#### <a name="to-download-the-content"></a>下載內容

1. 在 Help Viewer 中，選擇 [管理內容] 索引標籤。

2. 在 [建議的文件] 或 [可用的文件] 之下，巡覽至您想要下載的文件集，然後選擇 [新增]。

3. 選擇 [更新]。

接下來，您必須封裝內容，讓它可以部署到用戶端電腦。

#### <a name="to-package-the-content"></a>封裝內容

1. 建立複製內容的目標資料夾，以便稍後進行部署。 例如： *C:\VSHelp*。

2. 以系統管理員許可權開啟 *cmd.exe* 。

3. 巡覽至您在步驟 1 中建立的資料夾。

4. 輸入下列命令：

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o`

     例如：`Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>部署內容

1. 建立網路共用，並將這些說明內容複製到該位置。

     例如，將 *C:\VSHelp* 中的內容複寫到 *\\ \myserver\VSHelp*。

2. 建立 .bat 檔案，以包含說明內容的部署指令碼。 由於用戶端在推送的部分過程中要刪除的檔案可能有讀取鎖定，您應該在推送更新之前關閉用戶端。 例如：

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3. 在您要安裝說明內容的本機電腦上執行 *.bat* 檔案。

## <a name="see-also"></a>另請參閱

- [Help Content Manager 的命令列引數](../help-viewer/command-line-arguments.md)
- [Help Content Manager 覆寫](../help-viewer/behavior-overrides.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
- [Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md)
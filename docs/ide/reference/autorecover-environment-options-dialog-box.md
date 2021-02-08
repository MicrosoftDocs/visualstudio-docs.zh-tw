---
title: 選項對話方塊、環境、自動回復
description: 瞭解 [自動復原]、[環境]、[選項] 對話方塊，以及如何使用它來指定是否要自動備份檔案。
ms.custom: SEO-VS-2020
ms.date: 08/14/2020
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9a90198ce4cf3dc54eedbf80bbf4ffbad634cbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836484"
---
# <a name="autorecover-environment-options-dialog-box"></a>選項對話方塊、環境、自動回復

使用 [選項] 對話方塊的這個頁面，即可指定是否自動備份檔案。 如果 Visual Studio 意外關閉，您也可以指定是否要還原已修改的檔案。

若要存取此對話方塊，請移至 [**工具**  >  **選項**  >  **環境**  >  **自動** 回復]。

:::image type="content" source="media/autorecover-options.png" alt-text="[選項] 對話方塊中 [自動回復] 區段的螢幕擷取畫面":::

**每隔 [n] 分鐘儲存一次自動回復資訊**

::: moniker range="vs-2019"

使用此選項，可自訂在編輯器中自動儲存檔案的頻率。 針對先前儲存的檔案，Visual Studio 2019 16.2 版和更新版本會在 ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [專案名稱]*** 中儲存檔案的複本。 如果檔案是新檔案，但尚未儲存，Visual Studio 使用隨機產生的檔案名來 autosaves 它。

> [!NOTE]
> 如果您使用 Visual Studio 2019 16.1 版或更早版本，檔案位置是 *%USERPROFILE%\Documents\Visual Studio [version] \Backup Files \\ [專案名稱]*。 如需詳細資訊，請參閱 [Visual Studio 2019 版本資訊歷程記錄](/visualstudio/releases/2019/release-notes-history/) 頁面。

::: moniker-end

::: moniker range="vs-2017"

使用此選項，可自訂在編輯器中自動儲存檔案的頻率。 針對先前儲存的檔案，Visual Studio 2017 會將檔案的複本儲存在 *%USERPROFILE%\Documents\Visual Studio [version] \Backup files \\ [專案名稱]* 中。 如果檔案是新檔案，但尚未儲存，Visual Studio 使用隨機產生的檔案名來 autosaves 它。

::: moniker-end

**保留 [n] 天的自動回復資訊**

使用此選項，可指定 Visual Studio 保留針對自動回復所建立的檔案多久的時間。

### <a name="see-also"></a>另請參閱

- [選項對話方塊](../../ide/reference/options-dialog-box-visual-studio.md)

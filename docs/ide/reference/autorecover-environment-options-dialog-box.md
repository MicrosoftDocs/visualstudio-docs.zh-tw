---
title: 選項對話方塊、環境、自動回復
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81493379cf847251124d2ab4fd0a978abd96af8f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585661"
---
# <a name="autorecover-environment-options-dialog-box"></a>選項對話方塊、環境、自動回復

使用 [選項]**** 對話方塊的這個頁面，即可指定是否自動備份檔案。 如果 Visual Studio 意外關閉，您也可以指定是否要還原已修改的檔案。

選取 [工具]**** 功能表及 [選項]****，然後選取 [環境]**** > [自動回復]****，即可存取此對話方塊。 如果此頁面未出現在清單中，請在 [選項]**** 對話方塊中選取 [顯示所有設定]****。

**每 [n] 分鐘保存一次自動復原資訊**

使用此選項，可自訂在編輯器中自動儲存檔案的頻率。 針對先前儲存的檔案，檔案的複本會儲存在 %USERPROFILE%\Documents\Visual Studio\\[版本]\Backup Files\\[專案名稱]** 中。 若為新檔案，而且您尚未儲存，就會使用隨機產生的檔案名稱自動儲存檔案。

**將自動復原資訊保留 [n] 天**

使用此選項，可指定 Visual Studio 保留針對自動回復所建立的檔案多久的時間。

### <a name="see-also"></a>另請參閱

- [選項對話方塊](../../ide/reference/options-dialog-box-visual-studio.md)

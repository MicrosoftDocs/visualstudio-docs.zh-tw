---
title: 選項對話方塊、環境、自動回復 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 743543e03806a842eabc2bbfc69011d63b1264d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660971"
---
# <a name="autorecover-environment-options-dialog-box"></a>選項對話方塊、環境、自動回復
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用 [選項] 對話方塊的這個頁面，即可指定是否自動備份檔案。 此頁面也可讓您指定是否在整合式開發環境 (IDE) 意外關閉時還原已修改的檔案。 選取 [工具]**** 功能表，並選擇 [選項]****，然後選取 [環境]**** 資料夾，再選擇 [自動回復]**** 頁面，即可存取此對話方塊。 如果此頁面未出現在清單中，請在 [選項]**** 對話方塊中選取 [顯示所有設定]****。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

 **每 \<n> 分鐘儲存一次自動回復資訊** ：使用此選項可自訂在編輯器中自動儲存檔案的頻率。 針對先前儲存的檔案，會將檔案的複本儲存在 \\ ..\My Documents\Visual Studio \<*version*> \Backup files \\ < *專案名稱*> 中。 如果是新檔案，而且尚未手動儲存，就會使用隨機產生的檔案名稱自動儲存檔案。

 **保留自動復原資訊的 \<n> 天數：** 使用此選項來指定 Visual Studio 保留為自動復原而建立之檔案的時間長度。

## <a name="see-also"></a>另請參閱
 [選項對話方塊](../../ide/reference/options-dialog-box-visual-studio.md)

---
title: "選項對話方塊、環境、自動回復 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 320b31b01237656be157be9ad9ce5787521215db
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="autorecover-environment-options-dialog-box"></a>選項對話方塊、環境、自動回復
使用 [選項] 對話方塊的這個頁面，即可指定是否自動備份檔案。 此頁面也可讓您指定是否在整合式開發環境 (IDE) 意外關閉時還原已修改的檔案。 選取 [工具] 功能表，並選擇 [選項]，然後選取 [環境] 資料夾，再選擇 [自動回復] 頁面，即可存取此對話方塊。 如果此頁面未出現在清單中，請在 [選項] 對話方塊中選取 [顯示所有設定]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。  
  
 **儲存自動回復資訊時間間隔: \<n> 分鐘**  
 使用此選項，可自訂在編輯器中自動儲存檔案的頻率。 對於先前儲存的檔案，檔案的複本儲存在 \\...\My Documents\Visual Studio \<版本>\Backup Files\\<專案名稱> 中。 如果是新檔案，而且尚未手動儲存，就會使用隨機產生的檔案名稱自動儲存檔案。  
  
 **自動回復資訊保留期限: \<n> 天**  
 使用此選項，可指定 Visual Studio 保留針對自動回復所建立的檔案多久的時間。  
  
## <a name="see-also"></a>另請參閱  
 [選項對話方塊](../../ide/reference/options-dialog-box-visual-studio.md)

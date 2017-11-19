---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-vsct-file
title: "使用修改 Isolated 的 Shell。Vsct 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3290e33ac473c6914437f8ef036ec8047f46e063
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>使用修改 Isolated 的 Shell。Vsct 檔案
UI 專案，Visual Studio 隔離的 shell 專案包含.vsct 檔案，可讓您指定哪些應用程式群組和個別的命令可用於應用程式。 以下是未修改的.vsct 檔案的摘錄。  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 根據預設，大部分的命令和命令群組會包含。 若要排除的命令或指令群組，只要取消註解該命令或群組。  
  
 例如，若要移除的下一個窗格和上一個窗格的命令，請取消註解`No_PaneNextPaneCommand`和`No_PanePrevPaneCommand`項目：  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 如需更詳細範例這些自訂，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="referenced-files"></a>參考的檔案  
 應用程式的預設.vsct 檔參考的下列檔案。 這些檔案位於 Visual Studio SDK 安裝目錄的 \VisualStudioIntegration\Common\Inc\ 子目錄中。  
  
|檔案|說明|  
|----------|-----------------|  
|wbids.h|Web 瀏覽封裝 UI 身分識別。|  
|AppIDCmdUsed.vsct|主要的 Visual Studio UI 元素的命令資料表。|  
|EmulatorCmdUsed.vsct|Emacs 和簡短編輯器模擬 UI 元素的命令資料表。|  
|Vsdebugguids.h|定義命令、 選項 頁面上和其他功能的 Visual Studio 偵錯工具的 Guid。|  
|VsDbgCmdUsed.vsct|偵錯工具的命令資料表。|  
  
 AppIDCmdUsed.vsct 檔案包含 Visual Studio UI 項目，根據應用程式.vsct 檔中定義的符號。  
  
 如需詳細資訊，請參閱[設計 XML 命令資料表 (。Vsct) 檔案](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)和[VSCT XML 結構描述參考](../extensibility/vsct-xml-schema-reference.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)
---
title: 使用來修改隔離式 Shell。.Vsct 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194228"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>使用 .Vsct 檔案修改 Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 獨立模式 shell 專案的 UI 專案包含 .vsct 檔案，可讓您指定應用程式中可用的應用程式群組和個別命令。 以下是來自未修改之 .vsct 檔案的摘錄。  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 依預設，會包含大部分的命令和命令群組。 若要排除命令或命令群組，只要將該命令或群組取消批註即可。  
  
 例如，若要移除下一個窗格和先前的窗格命令，請將 `No_PaneNextPaneCommand` 和專案取消批註 `No_PanePrevPaneCommand` ：  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 如需這些自訂的更詳細範例，請參閱 [逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="referenced-files"></a>參考的檔案  
 應用程式的預設 .vsct 檔案會參考下列檔案。 這些檔案位於 Visual Studio SDK 安裝目錄的 \VisualStudioIntegration\Common\Inc\ 子目錄中。  
  
|檔案|描述|  
|----------|-----------------|  
|wbids。h|網頁流覽套件的 UI 身分識別。|  
|AppIDCmdUsed. .vsct|主要 Visual Studio UI 元素的命令資料表。|  
|EmulatorCmdUsed. .vsct|Emacs 和簡單編輯器模擬 UI 元素的命令資料表。|  
|Vsdebugguids。h|定義命令的 Guid、選項頁面，以及 Visual Studio 偵錯工具的其他功能。|  
|VsDbgCmdUsed. .vsct|偵錯工具的命令資料表。|  
  
 AppIDCmdUsed. .vsct 檔案包含以 .vsct 檔案中定義的符號為基礎的 Visual Studio UI 元素。  
  
 如需詳細資訊，請參閱 [設計 XML 命令表格 (。.Vsct) ](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) 檔和 [.Vsct XML 架構參考](../extensibility/vsct-xml-schema-reference.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)

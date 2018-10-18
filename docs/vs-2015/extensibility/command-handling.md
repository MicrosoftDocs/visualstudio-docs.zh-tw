---
title: 命令處理 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de4bf6ace6860cbd6155fe67a0de824e5626cfe3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257214"
---
# <a name="command-handling"></a>命令處理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您的編輯器可以定義新的命令。 命令通常會顯示在功能表中，在工具列上，或內容功能表中。  
  
 如需定義命令和功能表的詳細資訊，請參閱 <<c0> [ 命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 語言服務可以控制哪些內容功能表會顯示在編輯器中，攔截<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>列舉型別。 或者，您可以控制每個標記為基礎的內容功能表。 如需詳細資訊，請參閱[語言服務篩選器的重要命令](../extensibility/internals/important-commands-for-language-service-filters.md)。  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>將命令加入至編輯器操作功能表  
 若要將命令新增至內容功能表中，您必須先定義一組屬於特定群組的功能表命令。 下列範例取自.vsct 檔案中產生的逐步解說[逐步解說： 新增功能至自訂編輯器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<功能表的 guid ="guidCustomEditorCmdSet"id ="IDMX_RTF 」 優先順序 ="0x0000"type = [內容] >  
  
 \<父 guid ="guidCustomEditorCmdSet"id ="0"/ >  
  
 \<字串 >  
  
 \<ButtonText > CustomEditor 快顯功能表\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ 字串 >  
  
 \</ 功能表 >  
  
 \</ 功能表 >  
  
 上述的文字加入文字的內容功能表命令**CustomEditor 快顯功能表**。 命令集的建立與這個編輯器，，和型別就是 [內容] 功能表的 GUID。  
  
 您也可以使用預先定義的命令不需要定義在.vsct 檔案中。 例如，如果您檢查 Visual Studio Package 範本所產生的 EditorPane.cs 檔案時，您可找到一組預先定義的命令，像是<xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID>所定義<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>，例如 onSelectAll 方法的命令處理常式中處理。  
  
## <a name="see-also"></a>另請參閱  
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)


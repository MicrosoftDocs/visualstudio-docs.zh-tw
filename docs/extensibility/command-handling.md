---
title: "命令處理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3ecbff62570067b25aae9ad525138687eb281c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="command-handling"></a>命令處理
您的編輯器可以定義新的命令。 命令通常會顯示在功能表中，在工具列上，或內容功能表中。  
  
 如需有關如何定義命令和功能表的詳細資訊，請參閱[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 語言服務可以控制哪些內容功能表會顯示在編輯器中，攔截<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>列舉型別。 或者，您可以控制每個標記為基礎的內容功能表。 如需詳細資訊，請參閱[重要命令語言服務篩選](../extensibility/internals/important-commands-for-language-service-filters.md)。  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>將命令加入至編輯器內容功能表  
 若要加入至內容功能表的命令，您必須先定義一組屬於特定群組的功能表命令。 下列範例取自.vsct 檔產生為部分的逐步解說[逐步解說： 加入功能與自訂編輯器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<功能表 guid ="guidCustomEditorCmdSet"id ="IDMX_RTF"priority ="0x0000"type = [內容] >  
  
 \<父 guid ="guidCustomEditorCmdSet"id ="0"/ >  
  
 \<字串 >  
  
 \<ButtonText > CustomEditor 操作功能表\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ 字串 >  
  
 \</ 功能表 >  
  
 \</ 功能表 >  
  
 上述的文字加入操作功能表命令的文字**CustomEditor 操作功能表**。 命令集的建立與這個編輯器，，而此類型是 [內容] 功能表的 GUID。  
  
 您也可以使用預先定義的命令不需要在.vsct 檔案中定義。 例如，如果您檢查 Visual Studio 封裝範本所產生的 EditorPane.cs 檔案，您發現一組預先定義的命令，例如<xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID>所定義<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>，會在命令處理常式，例如 onSelectAll 方法處理。  
  
## <a name="see-also"></a>請參閱  
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)
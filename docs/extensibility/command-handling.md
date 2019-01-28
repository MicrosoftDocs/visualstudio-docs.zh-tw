---
title: 命令處理 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3f9086bba7d5c5adfa42f1297de07a2f50ff7e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988125"
---
# <a name="command-handling"></a>命令處理
您的編輯器可以定義新的命令。 命令通常會顯示在功能表中，在工具列上，或內容功能表中。  
  
 如需定義命令和功能表的詳細資訊，請參閱 <<c0> [ 命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 語言服務可以控制哪些內容功能表會顯示在編輯器中，攔截<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>列舉型別。 或者，您可以控制每個標記為基礎的內容功能表。 如需詳細資訊，請參閱 <<c0> [ 語言服務篩選器的重要命令](../extensibility/internals/important-commands-for-language-service-filters.md)。  
  
## <a name="add-commands-to-the-editor-context-menu"></a>將命令加入至編輯器操作功能表  
 若要將命令新增至內容功能表中，您必須先定義一組屬於特定群組的功能表命令。 下列範例取自 *.vsct*逐步解說的一部分產生檔案[逐步解說：將功能加入至自訂編輯器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText > CustomEditor 快顯功能表\</ButtonText >  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 上述的文字加入文字的內容功能表命令**CustomEditor 快顯功能表**。 功能表的 GUID 是建立與這個編輯器的命令集的一部分。 此類型為 [內容]。  
  
 您也可以使用預先定義的命令不需要定義於 *.vsct*檔案。 例如，檢查*EditorPane.cs* Visual Studio Package 範本所產生的檔案。 您會發現一組預先定義的命令，例如<xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID>所定義<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>，在命令處理常式中的這類處理`onSelectAll`方法。  
  
## <a name="see-also"></a>另請參閱  
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
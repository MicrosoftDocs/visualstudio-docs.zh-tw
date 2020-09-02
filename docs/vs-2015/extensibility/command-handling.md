---
title: 命令處理 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184379"
---
# <a name="command-handling"></a>命令處理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您的編輯器可以定義新的命令。 命令通常會顯示在功能表、工具列或內容功能表中。  
  
 如需有關定義命令和功能表的詳細資訊，請參閱 [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 語言服務可以藉由攔截列舉，來控制編輯器中顯示的內容功能表 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 。 或者，您可以根據每個標記來控制內容功能表。 如需詳細資訊，請參閱 [語言服務篩選的重要命令](../extensibility/internals/important-commands-for-language-service-filters.md)。  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>將命令加入編輯器內容功能表  
 若要將命令新增至內容功能表，您必須先定義一組屬於特定群組的功能表命令。 下列範例取自逐步解說 [逐步解說：將功能新增至自訂編輯器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)中所產生的 .vsct 檔案：  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText>CustomEditor 內容功能表\</ButtonText>  
  
 \<CommandName>CustomEditorCoNtextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 上述文字會新增具有文字 **CustomEditor 內容功能表**的內容功能表命令。 功能表 GUID 是使用此編輯器建立的命令集，且類型為「內容」。  
  
 您也可以使用不需要在 .vsct 檔案中定義的預先定義命令。 例如，如果您檢查 Visual Studio 套件範本所產生的 EditorPane.cs 檔，您會發現一組預先定義的命令（例如 <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> 定義的命令） <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> 會在命令處理常式（例如 onSelectAll 方法）中處理。  
  
## <a name="see-also"></a>另請參閱  
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)

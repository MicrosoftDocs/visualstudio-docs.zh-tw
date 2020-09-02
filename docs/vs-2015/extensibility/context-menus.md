---
title: 內容功能表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184274"
---
# <a name="context-menus"></a>操作功能表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當使用者以滑鼠右鍵按一下工作區的使用中區域，並清除滑鼠右鍵放開時，就會顯示內容功能表。  
  
## <a name="editor-context-menus"></a>編輯器操作功能表  
 藉由攔截 `ECMD_SHOWCONTEXTMENU` ，您的語言服務可以控制要在編輯器中顯示的內容功能表。 若要顯示您自己的內容功能表，請在呼叫時處理此命令 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> 。 如果您未處理此命令，則 IDE 會顯示為編輯器提供的標準內容功能表。 您也可以根據每個標記來控制內容功能表的內容。 如需這方面的詳細資訊，請參閱 [使用文字標記搭配舊版 API](../extensibility/using-text-markers-with-the-legacy-api.md) 和 [攔截舊版語言服務命令](../extensibility/internals/intercepting-legacy-language-service-commands.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)   
 [延伸功能表和命令](../extensibility/extending-menus-and-commands.md)

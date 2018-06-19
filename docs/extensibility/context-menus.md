---
title: 內容功能表 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa957e949127663eca7d4e619919edcc07c7a29b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108556"
---
# <a name="context-menus"></a>操作功能表
操作功能表時使用者以滑鼠右鍵按一下工作區的使用中的區域中，會顯示，並清除且放開滑鼠按鈕。  
  
## <a name="editor-context-menus"></a>編輯器操作功能表  
 藉由攔截`ECMD_SHOWCONTEXTMENU`，語言服務可以控制會顯示在編輯器的操作功能表。 若要顯示您自己的內容功能表，此命令時處理傳遞到您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>。 如果您不處理這個命令，IDE 會顯示標準的操作功能表提供的編輯器。 您也可以控制每個標記為基礎的內容功能表的內容。 如需詳細資訊，請參閱[具有舊版應用程式開發介面使用的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)和[攔截舊版語言服務命令](../extensibility/internals/intercepting-legacy-language-service-commands.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)   
 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
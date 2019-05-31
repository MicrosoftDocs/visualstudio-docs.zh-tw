---
title: 操作功能表 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5534d0895e35e252364b491858a694a1f5b726a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341725"
---
# <a name="context-menus"></a>操作功能表
操作功能表會顯示當使用者以滑鼠右鍵按一下的作用中區域的工作區中，並清除 當使用者放開滑鼠右按鈕。

## <a name="editor-context-menus"></a>編輯器操作功能表
 藉由攔截`ECMD_SHOWCONTEXTMENU`，語言服務可以控制將會顯示在編輯器中的操作功能表。 若要顯示您自己的操作功能表，請處理此命令時傳遞至您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>。 如果您並未處理這個命令，IDE 會顯示標準的操作功能表提供的編輯器。 您也可以控制每個標記為基礎的內容功能表的內容。 如需詳細資訊，請參閱[在舊版的 API 中使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)並[攔截舊版語言服務命令](../extensibility/internals/intercepting-legacy-language-service-commands.md)。

## <a name="see-also"></a>另請參閱
- [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)
- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
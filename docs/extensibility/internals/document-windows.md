---
title: 文件視窗 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708507"
---
# <a name="document-windows"></a>文件視窗
在 Visual Studio 中,*文件視窗*是與多文檔介面 (MDI) 視窗關聯的框架子視窗。 文件視窗通常用於顯示和修改原始碼或文本,但它們還可以承載其他功能類型。 文件視窗:

- 可以組織在父 MDI 中的單獨水準或垂直選項卡組中,以便可以同時查看多個檔。

- 可以按父 MDI 中的任何順序停靠。

- 可以自由浮動。

- 按選項卡順序連結到其他 MDI 視窗。

  在文件視窗選項卡的快捷功能表上可以找到用於分組、停靠和浮動的命令。

  有關視覺化工作室中視窗行為的詳細資訊,請參閱[自訂視窗佈局](../../ide/customizing-window-layouts-in-visual-studio.md)。

## <a name="document-window-implementation"></a>文件視窗實現
 文件視窗是通過實現編輯器創建的。 該<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面創建文檔視窗作為實例化編輯器的一部分。 有關詳細資訊,請參閱[編輯器中的舊介面](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)。

> [!NOTE]
> 要在視窗中提供前後導航點,請<xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation>實現介面。 文字編輯器使用文字標記來標識文檔中的導航點。

## <a name="the-running-document-table"></a>執行的文件表
 IDE 使用正在執行的文件表 (RDT) 來追蹤每個文件視窗的狀態。 RDT 是通知文檔視窗事件的機制,例如關閉解決方案或編輯檔時。 有關詳細資訊,請參閱[執行文件表](../../extensibility/internals/running-document-table.md)。

## <a name="see-also"></a>另請參閱
- [延遲的文件載入](../../extensibility/internals/delayed-document-loading.md)

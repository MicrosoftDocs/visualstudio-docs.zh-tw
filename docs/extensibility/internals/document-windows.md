---
title: 檔視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d29d64090320a8f62491209773145c024564efa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186616"
---
# <a name="document-windows"></a>文件視窗
在 Visual Studio 中，*文件視窗*是與多重文件介面（MDI）視窗相關聯的框架子視窗。 檔視窗通常用來顯示和修改原始程式碼或文字，但也可以裝載其他功能類型。 文件視窗：

- 可以組織成父 MDI 中的個別水準或垂直索引標籤群組，讓多個檔案可以同時查看。

- 可以在父 MDI 中以任何順序停駐。

- 可以自由浮動。

- 會連結至其他 MDI 視窗的定位順序。

  [群組]、[停駐] 和 [浮動] 的命令可以在文件視窗索引標籤的快捷方式功能表上找到。

  如需 Visual Studio 中視窗行為的詳細資訊，請參閱[自訂視窗版面](../../ide/customizing-window-layouts-in-visual-studio.md)配置。

## <a name="document-window-implementation"></a>文件視窗的執行
 檔視窗是藉由執行編輯器來建立的。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 介面會在具現化編輯器的過程中建立文件視窗。 如需詳細資訊，請參閱[編輯器中的舊版介面](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)。

> [!NOTE]
> 若要在視窗中提供向後和向前流覽點，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> 介面。 文字編輯器會使用文字標記來識別檔中的導覽點。

## <a name="the-running-document-table"></a>執行中的檔資料表
 IDE 會使用執行中的檔資料表（RDT）來追蹤每個文件視窗的狀態。 RDT 是文件視窗收到事件通知的機制，例如當解決方案關閉或已編輯檔案時。 如需詳細資訊，請參閱執行[檔資料表](../../extensibility/internals/running-document-table.md)。

## <a name="see-also"></a>請參閱
- [延遲的檔載入](../../extensibility/internals/delayed-document-loading.md)
---
title: 文件 Windows |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d53cb3298ec3a8190f79ad87bd89e646ccbafbe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633209"
---
# <a name="document-windows"></a>文件視窗
在 Visual Studio 中，*文件視窗*是相關聯的多重文件介面 (MDI) 視窗框架的子視窗。 文件視窗通常用於顯示和修改的原始碼或文字，但它們也可以裝載其他功能的類型。 文件視窗：

- 可以組織 MDI 父項中的另一個水平或垂直索引標籤群組中，以便可以同時檢視多個檔案。

- 可以停駐在 MDI 父代中的任何順序。

- 可以是自由浮動。

- 會連結到其他的 MDI 視窗的定位順序中。

  群組的命令，停駐和浮動都位於文件視窗索引標籤的捷徑功能表。

  如需有關在 Visual Studio 中的視窗行為的詳細資訊，請參閱 <<c0> [ 自訂視窗版面配置](../../ide/customizing-window-layouts-in-visual-studio.md)。

## <a name="document-window-implementation"></a>文件視窗實作
 藉由實作編輯器建立文件視窗。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面建立的具現化編輯器一部分的文件視窗。 如需詳細資訊，請參閱 <<c0> [ 舊版介面在編輯器中](../../extensibility/legacy-interfaces-in-the-editor.md)。

> [!NOTE]
>  若要提供向後和向前瀏覽 視窗中的點，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation>介面。 文字編輯器會使用文字標記來識別瀏覽文件中的點。

## <a name="the-running-document-table"></a>執行文件資料表
 IDE 會使用執行文件資料表 (RDT) 來追蹤每個文件視窗的狀態。 RDT 是透過哪份文件視窗會收到通知的事件，例如方案已關閉時，或已編輯檔案的機制。 如需詳細資訊，請參閱 <<c0> [ 執行文件表格](../../extensibility/internals/running-document-table.md)。

## <a name="see-also"></a>另請參閱
- [延遲載入文件](../../extensibility/internals/delayed-document-loading.md)
---
title: 文件視窗 |Microsoft Docs
description: 瞭解 Visual Studio 中的文件視窗，包括如何執行這些工作，以及執行中的檔資料表 (RDT) 追蹤其狀態的方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f62a6cc4f7b217bbcf8c94b437bcd7ce9d0d1b2b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946731"
---
# <a name="document-windows"></a>文件視窗
在 Visual Studio 中， *文件視窗* 是與多重文件介面（ (MDI) 視窗）相關聯的框架子視窗。 文件視窗通常是用來顯示和修改原始程式碼或文字，但也可以裝載其他功能類型。 文件視窗：

- 可以在父 MDI 的不同水準或垂直索引標籤群組中組織，如此一來，就可以同時查看多個檔案。

- 可以停駐在父 MDI 的任何順序中。

- 可以自由浮動。

- 會以定位順序連結到其他 MDI 視窗。

  您可以在 [文件視窗] 索引標籤的快捷方式功能表上，找到群組、停駐和浮動的命令。

  如需 Visual Studio 中視窗行為的詳細資訊，請參閱 [自訂視窗版面](../../ide/customizing-window-layouts-in-visual-studio.md)配置。

## <a name="document-window-implementation"></a>檔視窗執行
 檔視窗是藉由執行編輯器來建立。 介面會在具現 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 化編輯器的過程中建立文件視窗。 如需詳細資訊，請參閱 [編輯器中的舊版介面](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)。

> [!NOTE]
> 若要在視窗中提供反向和向前導覽點，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> 介面。 文字編輯器會使用文字標記來識別檔中的導覽點。

## <a name="the-running-document-table"></a>執行中的檔資料表
 IDE 會使用執行中的檔資料表 (RDT) 來追蹤每個文件視窗的狀態。 RDT 是一種機制，可讓文件視窗收到事件的通知，例如當關閉方案時，或是在編輯檔案時。 如需詳細資訊，請參閱執行 [檔資料表](../../extensibility/internals/running-document-table.md)。

## <a name="see-also"></a>另請參閱
- [延遲的檔載入](../../extensibility/internals/delayed-document-loading.md)

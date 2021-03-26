---
title: 自訂編輯器中的檔資料和檔查看 |Microsoft Docs
description: 瞭解自訂編輯器的元件，也就是檔資料物件和檔視圖物件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 391bec513f1f6d32d7ff2f87d70abdbf491ab8be
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091236"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>自訂編輯器中的檔資料和檔查看
自訂編輯器是由兩個部分所組成：檔資料物件和檔視圖物件。 顧名思義，檔資料物件代表要顯示的文字資料。 同樣地，[檔視圖] 物件 (或 [view] ) 代表要顯示檔資料物件的一或多個視窗。

## <a name="document-data-object"></a>Document data 物件
 檔資料物件是文字緩衝區中文字的資料標記法。 它是儲存檔文字和其他資訊的 COM 物件。 檔資料物件也會處理檔的持續性，並啟用其資料的多個資料檢視。 如需相關資訊，請參閱

 <xref:EnvDTE80.Window2.DocumentData%2A> 和 [文件視窗](../extensibility/internals/document-windows.md)。

 自訂編輯器和設計工具可以選擇使用 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 物件或自己的自訂緩衝區。 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 遵循標準編輯器的簡化內嵌模型、支援多個視圖，並提供用來管理多個視圖的事件介面。

## <a name="document-view-object"></a>Document view 物件
 顯示程式碼和其他文字的視窗稱為「檔查看」或「視圖」。 當您建立編輯器時，您可以選擇單一視圖，其中的文字會顯示在單一視窗中。 或者，您可以選擇多個視圖，其中的文字會顯示在一個以上的視窗中。 您的選擇取決於您的應用程式。 例如，如果您需要並排編輯，您可以選擇多個 view。 每個視圖都與整合式開發環境 (IDE) 執行檔資料表 (RDT) 中的專案相關聯。 View windows 屬於專案或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 物件。

 如果您的編輯器支援多個檔資料物件的視圖，則您的檔資料和檔視圖物件必須是獨立的。 否則，可以將它們群組在一起。 如需詳細資訊，請參閱 [支援多個檔的觀點](../extensibility/supporting-multiple-document-views.md)。

 當包含檔的方案) 藉由比對執行中的檔資料表中每個專案的專案識別碼 (ItemID) 時，IDE 就會通知有關事件的視圖 (例如，當包含檔的方案關閉。 如需有關這個的詳細資訊，請參閱執行 [檔資料表](../extensibility/internals/running-document-table.md)。

 有兩個選項可用於建立自訂編輯器的視圖。 其中一個是就地啟動模型，在此模型中，會使用 ActiveX 控制項或檔資料物件將視圖託管于視窗中。 第二個是簡化的內嵌模型，其中的視圖由裝載， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 並且會實作為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 處理視窗命令。 如需就地啟用模型的相關資訊，請參閱就地 [啟用](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015)。 如需簡化內嵌模型的相關資訊，請參閱 [簡化](../extensibility/simplified-embedding.md)內嵌。

## <a name="see-also"></a>另請參閱

- [支援多個檔視圖](../extensibility/supporting-multiple-document-views.md)
- [簡化嵌入](../extensibility/simplified-embedding.md)
- [如何：將視圖附加至檔資料](../extensibility/how-to-attach-views-to-document-data.md)
- [檔鎖定持有者管理](../extensibility/document-lock-holder-management.md)
- [單一和多重索引標籤視圖](../extensibility/single-and-multi-tab-views.md)
- [儲存標準檔](../extensibility/internals/saving-a-standard-document.md)
- [持續性與執行中的檔資料表](../extensibility/internals/persistence-and-the-running-document-table.md)
- [判斷哪一個編輯器在專案中開啟檔案](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
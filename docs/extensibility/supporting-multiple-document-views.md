---
title: 支援多個檔視圖 |Microsoft Docs
description: 瞭解如何在 Visual Studio SDK 中，針對自訂編輯器使用個別的檔資料和檔視圖物件，以提供多個檔的觀點。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e54ee028c6a7db2d5d2ea1ab609be6c2887c9829
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056203"
---
# <a name="supporting-multiple-document-views"></a>支援多個文件檢視
您可以為編輯器建立個別的檔資料和檔視圖物件，以提供多個檔的觀點。 有些情況下，其他檔視圖會很有用：

- 新的視窗支援：您希望編輯器提供兩個或多個相同類型的視圖，讓已經在編輯器中開啟視窗的使用者可以從 [**視窗]** 功能表選取 [**新增視窗]** 命令，以開啟新視窗。

- 表單和程式碼視圖支援：您希望編輯器提供不同類型的觀點。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]例如，提供表單檢視和程式碼視圖。

  如需這項操作的詳細資訊，請參閱 Visual Studio 套件範本所建立之自訂編輯器專案中 EditorFactory .cs 檔案中的 CreateEditorInstance 程式。 如需此專案的詳細資訊，請參閱 [逐步解說：建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)。

## <a name="synchronizing-views"></a>同步處理視圖
 當您執行多個視圖時，檔資料物件會負責保持所有視圖與資料同步。 您可以使用上的事件處理介面 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ，將多個資料檢視與資料同步。

 如果您不使用 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 物件來同步處理多個視圖，則必須執行您自己的事件系統來處理對檔資料物件所做的變更。 您可以使用不同的資料細微性層級，讓多個視圖維持在最新狀態。 使用最大的資料細微性設定時，當您在其中一個視圖中輸入時，其他的視圖會立即更新。 使用最小的資料細微性時，不會更新其他視圖，直到它們啟動為止。

## <a name="determining-whether-document-data-is-already-open"></a>判斷檔資料是否已經開啟
 在整合式開發環境中，執行中的檔資料表 (RDT)  (IDE) 有助於追蹤檔的資料是否已經開啟，如下圖所示。

 ![DocDataView 圖形](../extensibility/media/docdataview.gif "Docdataview") 多個視圖

 依預設，每個 view (document view 物件) 都包含在自己的視窗框架 (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>) 中。 不過，如先前所述，檔資料可以顯示在多個視圖中。 若要啟用此功能，Visual Studio 檢查 RDT，判斷是否已在編輯器中開啟有問題的檔。 當 IDE 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 以建立編輯器時，在參數中傳回的非 Null 值 `punkDocDataExisting` 表示檔已在其他編輯器中開啟。 如需有關 RDT 函數的詳細資訊，請參閱執行 [檔資料表](../extensibility/internals/running-document-table.md)。

 在您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 執行中，檢查傳回的檔資料物件， `punkDocDataExisting` 以判斷檔資料是否適用于您的編輯器。  (例如，HTML 編輯器只會顯示 HTML 資料。如有需要，請 ) ，您的編輯器 factory 應提供資料的第二個資料檢視。 如果 `punkDocDataExisting` 參數不是 `NULL` ，則可能是在另一個編輯器中開啟檔資料物件，或更可能的情況是，檔資料已在具有相同編輯器的不同視圖中開啟。 如果檔資料在編輯器 factory 不支援的不同編輯器中開啟，則 Visual Studio 無法開啟您的編輯器 factory。 如需詳細資訊，請參閱 [如何：將視圖附加至檔資料](../extensibility/how-to-attach-views-to-document-data.md)。

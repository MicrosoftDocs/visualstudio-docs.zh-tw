---
title: 支援多個文件檢視 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 78ddc7ed811086622454e31d12ca5f1324d00da5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141716"
---
# <a name="supporting-multiple-document-views"></a>支援多個文件檢視
您可以提供多個檢視的文件建立個別的文件資料和文件檢視物件的編輯器。 某些其他文件檢視，會很有用的情況如下：  
  
-   新的視窗支援： 您想要您提供的相同類型的兩個或多個檢視的編輯器，如此已在編輯器中開啟的視窗的使用者可以選取，開啟新視窗**新視窗**命令**視窗**功能表。  
  
-   表單和程式碼模式支援： 您想要您編輯器，可提供不同類型的檢視。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]例如，提供 表單檢視和程式碼檢視。  
  
 如需詳細資訊，請參閱 CreateEditorInstance 程序，在 Visual Studio 封裝範本所建立的自訂編輯器專案內 EditorFactory.cs 檔案中。 如需有關此專案的詳細資訊，請參閱[逐步解說： 建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)。  
  
## <a name="synchronizing-views"></a>同步處理的檢視  
 當您實作多個檢視時，文件資料物件負責保存所有的資料同步處理的檢視。 您可以使用的事件處理介面上<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>與資料同步處理多個檢視。  
  
 如果您未使用<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件同步處理多個檢視，則您必須實作自己的事件系統，以處理文件資料物件所做的變更。 您可以使用不同的資料粒度層級，讓多個檢視保持在最新狀態。 使用設定的最大的資料粒度時，當您在一個檢視中輸入其他檢視會立即更新。 最小的資料粒度，會在啟動之前，不會更新其他檢視。  
  
## <a name="determining-whether-document-data-is-already-open"></a>決定是否文件資料時已經開啟  
 整合式的開發環境 (IDE) 中執行中文件資料表 (RDT) 可協助您追蹤是否為文件的資料已經開啟，如下圖所示。  
  
 ![DocDataView 圖形](../extensibility/media/docdataview.gif "Docdataview")  
多個檢視  
  
 根據預設，每個檢視 （文件檢視物件） 包含在它自己的視窗框架 (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>)。 如先前所述，不過，文件資料可以顯示多個檢視中。 若要啟用此功能，Visual Studio 會檢查以判斷是否有問題的文件已經在編輯器中開啟 RDT。 當 IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>若要建立編輯器 中中, 都會傳回非 NULL 值`punkDocDataExisting`參數表示文件已在其他編輯器中開啟。 如需有關如何為 RDT 函式，請參閱[執行中的文件表格](../extensibility/internals/running-document-table.md)。  
  
 在您<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>實作中，檢查文件資料物件中傳回`punkDocDataExisting`來判斷文件資料是否適合您的編輯器。 （例如，僅 HTML 資料應該顯示的 HTML 編輯器。）如果適當，編輯器 factory 應該針對資料提供第二個檢視。 如果`punkDocDataExisting`參數不是`NULL`，很可能是文件資料物件是在另一個編輯器中，開啟或，更有可能，文件資料已在不同的檢視具有相同的編輯器中開啟。 如果文件資料是在編輯器 factory 不支援的其他編輯器中開啟，Visual Studio 無法開啟編輯器 factory。 如需詳細資訊，請參閱[如何： 附加至文件資料的檢視](../extensibility/how-to-attach-views-to-document-data.md)。
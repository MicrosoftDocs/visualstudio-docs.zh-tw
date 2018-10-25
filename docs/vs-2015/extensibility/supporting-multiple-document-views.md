---
title: 支援多個文件檢視 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91becc7afb7c236ebe9d6e08c1b8a221cb9f90fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826541"
---
# <a name="supporting-multiple-document-views"></a>支援多個文件檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以為您的編輯器建立個別的文件資料和文件檢視物件，以提供文件的多個檢視。 一些其他的文件檢視會很有用的案例如下：  
  
- 新的視窗支援： 您想要您的編輯器將提供的相同類型的兩個或多個檢視，如此已經在編輯器中開啟的視窗的使用者可以選取，開啟新視窗**開新視窗**命令**視窗**  功能表。  
  
- 表單和程式碼檢視的支援： 您想要您的編輯器，以提供不同類型的檢視。 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]例如，提供 表單檢視和程式碼檢視。  
  
  如需詳細資訊，請參閱 CreateEditorInstance 程序，在 Visual Studio 封裝範本所建立的自訂編輯器專案 EditorFactory.cs 檔案中。 如需有關此專案的詳細資訊，請參閱 <<c0> [ 逐步解說： 建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)。  
  
## <a name="synchronizing-views"></a>同步處理檢視  
 當您實作多個檢視時，文件資料物件負責保存所有同步處理資料的檢視。 您可以使用的事件上處理介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>資料與同步處理多個檢視。  
  
 如果您不要使用<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件同步處理多個檢視，，則您必須實作您自己的事件系統來處理文件資料物件所做的變更。 您可以使用不同層級的資料粒度，將多個檢視最新狀態。 使用設定的最大的資料粒度時，在一個檢視中輸入其他檢視會立即更新。 最小的資料粒度，會在啟動之前，不會更新其他檢視。  
  
## <a name="determining-whether-document-data-is-already-open"></a>判斷是否文件資料是尚未開啟  
 整合式的開發環境 (IDE) 中執行文件資料表 (RDT) 可協助追蹤文件的資料為已開啟，如下圖所示。  
  
 ![DocDataView 圖形](../extensibility/media/docdataview.gif "Docdataview")  
多個檢視  
  
 根據預設，每個檢視 （文件檢視物件） 包含在它自己的視窗框架 (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>)。 如先前所述，不過，文件資料可以顯示多個檢視中。 若要這麼做，Visual Studio 會檢查以判斷是否有問題的文件已經在編輯器中開啟 RDT。 當呼叫 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>若要建立的編輯器中, 都會傳回非 NULL 值`punkDocDataExisting`參數表示的文件已經在另一個編輯器中開啟。 如需有關如何為 RDT 函式，請參閱[執行文件表格](../extensibility/internals/running-document-table.md)。  
  
 在您<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>實作中，檢查文件資料物件中傳回`punkDocDataExisting`來判斷文件資料是否適合您的編輯器。 （例如，僅 HTML 資料應該顯示的 HTML 編輯器。）如果適用的話，您的編輯器 factory 應該為資料提供第二個檢視。 如果`punkDocDataExisting`參數不是`NULL`，很可能是，文件資料物件是在其他編輯器中開啟，或者更可能、 文件資料已在不同的檢視，具有相同的編輯器中開啟。 如果在您的編輯器 factory 不支援的其他編輯器中開啟的文件資料，Visual Studio 無法開啟您的編輯器 factory。 如需詳細資訊，請參閱 <<c0> [ 如何： 附加至文件資料的檢視](../extensibility/how-to-attach-views-to-document-data.md)。


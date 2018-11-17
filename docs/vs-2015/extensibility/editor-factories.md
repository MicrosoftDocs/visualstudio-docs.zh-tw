---
title: 編輯器 Factory |Microsoft Docs
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
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 74ea8d296db643e74654f9016c1f5bff4f34c6d8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809450"
---
# <a name="editor-factories"></a>編輯器 Factory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

編輯器 factory 建立編輯器的物件，並將它們放在視窗框架內，又稱為實體的檢視。 它會建立文件資料及建立編輯器和設計工具所需的文件檢視物件。 編輯器 factory，才能建立 Visual Studio 核心編輯器和任何標準的編輯器。 也可以使用編輯器 factory 來建立自訂編輯器。  
  
 您會藉由實作建立編輯器 factory<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。 下列範例說明如何實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>建立編輯器 factory:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 編輯器會開啟該編輯器所處理的檔案類型的第一次載入。 您可以選擇開啟特定的編輯器] 或 [預設的編輯器。 如果您選取預設的編輯器，整合式的開發環境 (IDE) 會決定正確的編輯器開啟，並再將它開啟。 如需詳細資訊，請參閱 <<c0> [ 判斷哪一個編輯器在專案中開啟檔案](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)。  
  
## <a name="registering-editor-factories"></a>登錄編輯器 Factory  
 您可以使用您已建立編輯器之前，您首先必須註冊其相關資訊，包括它可以處理的副檔名。  
  
 如果 VSPackage 以 managed 程式碼撰寫，您可以使用 Managed Package Framework (MPF) 方法<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>之後載入 VSPackage 註冊編輯器 factory。 如果 VSPackage 以 unmanaged 程式碼，則您必須使用登錄編輯器 factory<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>服務。  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>使用登錄編輯器 Factory 的 Managed 程式碼  
 您必須在您的 VSPackage 中註冊您的編輯器 factory`Initialize`方法。 第一次呼叫`base.Initialize`，然後呼叫<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>每個編輯器 factory  
  
 在 managed 程式碼沒有需要取消註冊的編輯器 factory，因為 VSPackage 會為您處理這。 此外，如果您的編輯器 factory 實作<xref:System.IDisposable>，取消註冊時，會自動會處置它。  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>使用 unmanaged 程式碼，以登錄編輯器 factory  
 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>編輯器套件，使用實作`QueryService`方法來呼叫`SVsRegisterEditors`。 執行此動作將指標傳回至<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>。 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>方法，傳遞您的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。 您必須 mplement<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>在個別的類別。  
  
## <a name="the-editor-factory-registration-process"></a>編輯器 Factory 註冊程序  
 Visual Studio 會載入您使用編輯器 factory 的編輯器時，就會發生下列處理程序：  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]專案系統呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
2.  這個方法會傳回編輯器 factory。 Visual Studio 延遲載入編輯器的封裝，不過，直到實際需要的專案系統的編輯器。  
  
3.  當專案系統需要編輯器時，Visual Studio 會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>，傳回的文件檢視和文件資料物件的特定的方法。  
  
4.  如果呼叫由 Visual Studio 編輯器 factory 使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>傳回文件資料物件和文件檢視物件、 Visual Studio 然後建立文件視窗中，置於文件檢視物件，並執行文件的項目資料表 (RDT) 文件資料物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [執行中的文件資料表](../extensibility/internals/running-document-table.md)


---
title: 編輯器 Factory |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 676918b6366837b6ee77cf27bd5fba9fbf608729
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128244"
---
# <a name="editor-factories"></a>編輯器 Factory
編輯器 factory 建立編輯器物件，並將它們放在視窗框架內，又稱為實體的檢視。 它會建立文件資料及建立編輯器和設計工具所需的文件檢視物件。 編輯器 factory，才能建立 Visual Studio 核心編輯器和任何標準的編輯器。 也可以使用編輯器 factory 建立自訂編輯器。  
  
 實作建立 editor factory<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。 下列範例說明如何實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>建立 editor factory:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 編輯器會開啟該編輯器所處理檔案類型的第一次載入。 您可以選擇特定的編輯器或預設編輯器開啟。 如果您選取的預設編輯器，整合式的開發環境 (IDE) 會判斷正確的編輯器開啟，並再將它開啟。 如需詳細資訊，請參閱[判斷哪一個編輯器在專案中開啟檔案](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)。  
  
## <a name="registering-editor-factories"></a>登錄編輯器 Factory  
 您可以使用您已建立的編輯器，您先必須登錄其相關資訊，包括它可以處理的副檔名。  
  
 如果 managed 程式碼中撰寫 VSPackage，您可以使用 Managed Package Framework (MPF) 方法<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>之後載入 VSPackage 登錄 editor factory。 如果您的 VSPackage 撰寫的 unmanaged 程式碼，則您必須使用登錄編輯器 factory<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>服務。  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>登錄 Editor Factory 使用 Managed 程式碼  
 您必須在您的 VSPackage 中註冊您的編輯器 factory`Initialize`方法。 第一次呼叫`base.Initialize`，然後呼叫<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>每個編輯器 factory  
  
 在 managed 程式碼，無須取消登錄 editor factory，因為 VSPackage 將為您處理這。 此外，如果您的編輯器 factory 實作<xref:System.IDisposable>，自動處置時取消註冊。  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>使用 unmanaged 程式碼中登錄 editor factory  
 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>實作您的編輯器套件，使用`QueryService`方法呼叫`SVsRegisterEditors`。 執行此動作將指標傳回至<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>。 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>藉由傳遞的實作方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。 您必須 mplement<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>在個別的類別。  
  
## <a name="the-editor-factory-registration-process"></a>編輯器 Factory 註冊程序  
 Visual Studio 載入使用編輯器 factory 編輯器時，就會發生下列處理序：  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案系統呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
2.  這個方法會傳回編輯器 factory。 Visual Studio 延遲載入編輯器的封裝，不過，直到實際需要的專案系統的編輯器。  
  
3.  當專案系統需求編輯器 中時，Visual Studio 會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>，傳回的文件檢視和文件資料物件的特製化的方法。  
  
4.  如果您編輯器 factory 使用 Visual Studio 會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>傳回文件資料物件和文件檢視物件，Visual Studio 然後建立文件視窗中，置於文件檢視物件，並插入文件中執行的項目資料表 (RDT) 供文件資料物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [執行中的文件資料表](../extensibility/internals/running-document-table.md)
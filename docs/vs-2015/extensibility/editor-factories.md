---
title: 編輯器工廠 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197756"
---
# <a name="editor-factories"></a>Editor Factory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

編輯器 factory 會建立編輯器物件，並將它們放在視窗框架（稱為實體視圖）中。 它會建立建立編輯器和設計工具所需的檔資料和檔視圖物件。 需要編輯器 factory 才能建立 Visual Studio core 編輯器和任何標準編輯器。 您也可以選擇性地使用編輯器 factory 來建立自訂編輯器。  
  
 您可以藉由執行介面來建立編輯器 factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 。 下列範例說明如何執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 以建立編輯器 factory：  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 當您第一次開啟該編輯器所處理的檔案類型時，就會載入編輯器。 您可以選擇開啟特定編輯器或預設編輯器。 如果您選取預設編輯器，整合式開發環境 (IDE) 會判斷要開啟的正確編輯器，然後開啟它。 如需詳細資訊，請參閱 [判斷哪個編輯器在專案中開啟](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)檔案。  
  
## <a name="registering-editor-factories"></a>註冊編輯器 factory  
 在您可以使用您所建立的編輯器之前，必須先註冊它的相關資訊，包括它可以處理的副檔名。  
  
 如果您的 VSPackage 是以 managed 程式碼撰寫，您可以在 VSPackage 載入後，使用 Managed Package Framework (MPF) 方法 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> 來註冊編輯器 factory。 如果您的 VSPackage 是以非受控碼撰寫，則您必須使用服務來註冊編輯器 factory <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> 。  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>使用 Managed 程式碼註冊編輯器 Factory  
 您必須在 VSPackage 的方法中註冊您的編輯器 factory `Initialize` 。 第一個呼叫 `base.Initialize` ，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> 每個編輯器 factory  
  
 在 managed 程式碼中，不需要取消註冊編輯器 factory，因為 VSPackage 將會為您處理這項工作。 此外，如果您的編輯器 factory <xref:System.IDisposable> 已完成，則會在取消註冊時自動加以處置。  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>使用非受控碼註冊編輯器 factory  
 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 編輯器封裝的執行中，請使用 `QueryService` 方法來呼叫 `SVsRegisterEditors` 。 這樣做會傳回的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> 。 藉 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 由傳遞您介面的實來呼叫方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 。 您必須 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 在不同的類別中 mplement。  
  
## <a name="the-editor-factory-registration-process"></a>編輯器 Factory 註冊程式  
 當 Visual Studio 使用編輯器 factory 載入編輯器時，會發生下列進程：  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]專案系統會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 。  
  
2. 這個方法會傳回編輯器 factory。 但是，在專案系統實際需要編輯器之前，Visual Studio 會延遲載入編輯器的封裝。  
  
3. 當專案系統需要編輯器時，Visual Studio 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ，這是一種會傳回檔視圖和檔資料物件的特殊方法。  
  
4. 如果透過 Visual Studio 呼叫您的編輯器 factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ，並同時傳回檔資料物件和檔視圖物件，Visual Studio 接著會建立文件視窗、將檔 view 物件放在其中，並在執行中的檔資料表中建立專案， (RDT 檔資料物件的) 。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [執行中的文件資料表](../extensibility/internals/running-document-table.md)

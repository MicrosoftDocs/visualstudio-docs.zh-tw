---
title: 調整至編輯器的舊版程式碼 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4fba22a2b2dacec57439b66abe6607c248ed1914
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926040"
---
# <a name="adapt-legacy-code-to-the-editor"></a>調整傳統的程式碼編輯器
Visual Studio 編輯器中有許多功能，您可以從現有的程式碼元件存取。 下列指示說明如何調整非 MEF 元件，例如，VSPackage，使用編輯器功能。 指示也會說明如何使用配接器在 managed 和 unmanaged 程式碼中取得編輯器的服務。  
  
## <a name="editor-adapters"></a>編輯器配接器  
 編輯器配接器或填充碼是包裝函式，也會公開的類別和介面中的編輯器物件<xref:Microsoft.VisualStudio.TextManager.Interop>API。 您可以使用配接器，例如非編輯器服務之間移動，Visual Studio shell 命令、 編輯器服務。 （這是編輯器目前裝載的方式在 Visual Studio 中）。配接器也可讓舊版編輯器和語言服務擴充功能在 Visual Studio 中正確運作。  
  
## <a name="use-editor-adapters"></a>使用編輯器配接器  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>提供新的編輯器介面和舊版的介面之間切換的方法，以及建立配接器的方法。  
  
 如果您在某個 MEF 元件組件中使用這項服務，可以匯入服務，如下所示。  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 如果您想要在非 MEF 元件中使用這項服務，請遵循本主題稍後的 「 使用 Visual Studio 編輯器服務在非 MEF 元件 」 一節中的指示。  
  
## <a name="switch-between-the-new-editor-api-and-the-legacy-api"></a>切換新編輯器 API 和舊版的 API  
 使用下列方法切換編輯器物件和舊版的介面。  
  
|方法|轉換|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|將轉換<xref:Microsoft.VisualStudio.Text.ITextBuffer>至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|將轉換<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>至<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|將轉換<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>至<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|將轉換<xref:Microsoft.VisualStudio.Text.Editor.ITextView>至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|將轉換<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>至<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。|  
  
## <a name="create-adapters"></a>建立配接器  
 您可以使用下列方法來建立舊版介面的介面卡。  
  
|方法|轉換|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|會建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>指定<xref:Microsoft.VisualStudio.Utilities.IContentType>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|會建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>針對<xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>建立 unmanaged 程式碼中的配接器  
 所有的配接器類別會註冊為本地共同建立，而且可以具現化使用`VsLocalCreateInstance()`函式。  
  
 所有配接器藉由使用中所定義的 Guid *vsshlids.h*中的檔案*\..\VisualStudioIntegration\Common\Inc\\*的 Visual Studio SDK 的資料夾安裝。 若要建立 VsTextBufferAdapter 的執行個體，請使用下列程式碼。  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="create-adapters-in-managed-code"></a>Managed 程式碼建立配接器  
 在 managed 程式碼，您可以在 unmanaged 程式碼所述的相同方式共同建立配接器。 您也可以使用 MEF 服務，可讓您建立和使用配接器互動。 取得配接器的這種方式可讓您更細微的控制與您共同建立時具備。  
  
### <a name="to-create-an-adapter-for-ivstextview"></a>若要建立用於 IVsTextView 配接器  
  
1.  將參考加入*Microsoft.VisualStudio.Editor.dll*。 請確定`CopyLocal`設為`false`。  
  
2.  具現化<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>、，如下所示。  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  呼叫 `CreateX()` 方法。  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="use-the-visual-studio-editor-directly-from-unmanaged-code"></a>使用 Visual Studio 編輯器，直接從 unmanaged 程式碼  
 Microsoft.VisualStudio.Platform.VSEditor 命名空間和 Microsoft.VisualStudio.Platform.VSEditor.Interop 命名空間公開 COM 可呼叫的介面為 IVx * 介面。 比方說，Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer 介面是 COM 版本的<xref:Microsoft.VisualStudio.Text.ITextBuffer>介面。 從`IVxTextBuffer`，您可以取得緩衝區的快照集的存取權、 緩衝區的修改，接聽的緩衝區上的文字變更事件並建立追蹤點和範圍。 下列步驟示範如何存取`IVxTextBuffer`從`IVsTextBuffer`。  
  
### <a name="to-get-an-ivxtextbuffer"></a>若要取得 IVxTextBuffer  
  
1.  定義 IVx\*介面位於*VSEditor.h*檔案中*\..\VisualStudioIntegration\Common\Inc\\* Visual studio 的資料夾SDK 安裝。  
  
2.  下列程式碼會具現化的文字緩衝區使用`IVsUserData->GetData()`方法。 下列程式碼中，`pData`是一個指向`IVsUserData`物件。  
  
    ```cpp  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="use-visual-studio-editor-services-in-a-non-mef-component"></a>-MEF 元件中使用 Visual Studio 編輯器服務  
 如果您有現有的 managed 程式碼元件，不會使用 MEF，而且您想要使用 Visual Studio 編輯器的服務，您必須加入包含 ComponentModelHost VSPackage 的組件的參考，並取得其 SComponentModel 服務。  
  
### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>若要使用 Visual Studio 編輯器元件，從非 MEF 元件  
  
1.  將參考加入*Microsoft.VisualStudio.ComponentModelHost.dll*中的組件*\..\Common7\IDE\\*的 Visual Studio 安裝資料夾。 請確定`CopyLocal`設為`false`。  
  
2.  新增私用`IComponentModel`您要使用 Visual Studio 編輯器服務，如下所示的類別的成員。  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  具現化元件模型，您的元件的初始化方法中。  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  在此之後，您可以取得任何其中一個 Visual Studio 編輯器服務藉由呼叫`IComponentModel.GetService<T>()`您想要服務的方法。  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```

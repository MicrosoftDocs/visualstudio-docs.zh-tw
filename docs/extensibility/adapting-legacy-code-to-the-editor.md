---
title: "改寫舊版程式碼編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03c0cbd20258618297e943524d06ba7b3a496264
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="adapting-legacy-code-to-the-editor"></a>改寫舊版程式碼編輯器
在 Visual Studio 編輯器具有許多功能，您可以從現有的程式碼元件存取。 下列指示說明如何調整非 MEF 元件，例如，VSPackage，若要使用編輯器功能。 指示也會示範如何取得編輯器的服務，在 managed 和 unmanaged 程式碼中使用配接器。  
  
## <a name="editor-adapters"></a>編輯器配接器  
 編輯器配接器或填充碼，是包裝函式也會公開的類別和介面中的編輯器物件<xref:Microsoft.VisualStudio.TextManager.Interop>應用程式開發介面。 您可以使用，例如移動非編輯器服務之間的介面卡、 Visual Studio shell 命令，以及編輯器服務。 （這是編輯器目前如何裝載 Visual Studio 中）。配接器也可讓舊版編輯器和語言服務延伸 Visual Studio 中正常運作。  
  
## <a name="using-editor-adapters"></a>使用編輯器配接器  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>提供新的編輯器介面和舊版的介面之間切換的方法和也建立配接器的方法。  
  
 如果您使用此服務 MEF 元件組件中，您可以如下所示匯入服務。  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 如果您想要在非 MEF 元件中使用這項服務，請遵循本主題稍後的 < 使用 Visual Studio 編輯器服務在非 MEF 元件 > 一節中的指示。  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>新編輯器 API 和舊版 API 之間切換  
 使用下列方法切換編輯器物件和傳統的介面。  
  
|方法|轉換|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|將轉換<xref:Microsoft.VisualStudio.Text.ITextBuffer>至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|將轉換<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>至<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|將轉換<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>至<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|將轉換<xref:Microsoft.VisualStudio.Text.Editor.ITextView>至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|將轉換<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>至<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。|  
  
## <a name="creating-adapters"></a>建立配接器  
 使用下列方法建立配接器，繼承的介面。  
  
|方法|轉換|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>指定<xref:Microsoft.VisualStudio.Utilities.IContentType>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>如<xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Unmanaged 程式碼中建立配接器  
 所有配接器類別登錄為本機共同建立的而且可以使用具現化`VsLocalCreateInstance()`函式。  
  
 所有介面卡會利用 vsshlids.h 檔中定義的 Guid 建立...Visual Studio SDK 安裝的 \VisualStudioIntegration\Common\Inc\ 資料夾。 若要建立 VsTextBufferAdapter 的執行個體，請使用下列程式碼。  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>在 Managed 程式碼建立配接器  
 在 managed 程式碼，您可以共同建立配接器所述的 unmanaged 程式碼相同的方式。 您也可以使用 MEF 服務，可讓您建立和使用配接器互動。 取得配接器的這種方式可讓更細部的掌控超過您擁有共同建立時。  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>若要建立的配接器的 IVsTextView  
  
1.  加入 Microsoft.VisualStudio.Editor.dll 的參考。 請確定`CopyLocal`設`false`。  
  
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
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>使用 Visual Studio 編輯器中，直接從 Unmanaged 程式碼  
 Microsoft.VisualStudio.Platform.VSEditor 命名空間和 Microsoft.VisualStudio.Platform.VSEditor.Interop 命名空間會為 IVx * 介面公開 COM 可呼叫的介面。 例如，Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer 介面是 COM 版本<xref:Microsoft.VisualStudio.Text.ITextBuffer>介面。 從`IVxTextBuffer`，您可以存取緩衝區快照集、 修改緩衝區、 接聽的緩衝區上的文字變更事件並建立追蹤點和範圍。 下列步驟示範如何存取`IVxTextBuffer`從`IVsTextBuffer`。  
  
#### <a name="to-get-an-ivxtextbuffer"></a>若要取得 IVxTextBuffer  
  
1.  IVx * 介面的定義檔中的 VSEditor.h 中...Visual Studio SDK 安裝的 \VisualStudioIntegration\Common\Inc\ 資料夾。  
  
2.  下列程式碼會具現化文字緩衝區使用`IVsUserData->GetData()`方法。 下列程式碼，`pData`是指向`IVsUserData`物件。  
  
    ```  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>在非 MEF 元件使用 Visual Studio 編輯器中的服務  
 如果您有現有的 managed 程式碼元件不會使用 MEF，而且您想要使用 Visual Studio 編輯器中的服務，您必須加入包含 ComponentModelHost VSPackage 的組件的參考，並取得其 SComponentModel 服務。  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>若要使用 Visual Studio 編輯器元件的非 MEF 元件  
  
1.  將參考加入 Microsoft.VisualStudio.ComponentModelHost.dll 組件中...\Common7\IDE\ 的 Visual Studio 安裝資料夾。 請確定`CopyLocal`設`false`。  
  
2.  加入私用`IComponentModel`您要使用 Visual Studio 編輯器服務，如下所示的類別的成員。  
  
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
  
4.  在此之後，您可以取得 Visual Studio 編輯器服務的任何一個呼叫`IComponentModel.GetService<T>()`方法您想要的服務。  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
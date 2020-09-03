---
title: 將舊版程式碼調整為編輯器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184911"
---
# <a name="adapting-legacy-code-to-the-editor"></a>使舊版程式碼配合編輯器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 編輯器有許多您可以從現有程式碼元件存取的功能。 下列指示說明如何調整非 MEF 元件（例如 VSPackage），以使用編輯器功能。 這些指示也會示範如何使用介面卡，在 managed 和非受控碼中取得編輯器的服務。  
  
## <a name="editor-adapters"></a>編輯器介面卡  
 編輯器介面卡（或填充碼）是編輯器物件的包裝函式，這些物件也會公開 API 中的類別和介面 <xref:Microsoft.VisualStudio.TextManager.Interop> 。 您可以使用介面卡在非編輯器服務間移動，例如 Visual Studio shell 命令和編輯器服務。  (這是編輯器目前裝載于 Visual Studio 的方式。 ) 的介面卡也可讓舊版編輯器和語言服務延伸模組在 Visual Studio 中正確運作。  
  
## <a name="using-editor-adapters"></a>使用編輯器介面卡  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>提供在新編輯器介面與舊版介面之間切換的方法，以及建立介面卡的方法。  
  
 如果您在 MEF 元件元件中使用此服務，您可以如下所示匯入服務。  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 如果您想要在非 MEF 元件中使用這項服務，請遵循本主題稍後的「在非 MEF 元件中使用 Visual Studio 編輯器服務」一節中的指示。  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>在新的編輯器 API 與舊版 API 之間切換  
 使用下列方法，在編輯器物件與舊版介面之間切換。  
  
|方法|轉換|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|將 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 轉換成 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|將 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 轉換成 <xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|將 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 轉換成 <xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|將 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 轉換成 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|將 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 轉換成 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。|  
  
## <a name="creating-adapters"></a>建立配接器  
 使用下列方法來建立舊版介面的介面卡。  
  
|方法|轉換|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>為指定的建立 <xref:Microsoft.VisualStudio.Utilities.IContentType> 。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 的 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>建立非受控程式碼中的介面卡  
 所有的介面卡類別都會註冊為本機共同可共用的，而且可以使用函式具現化 `VsLocalCreateInstance()` 。  
  
 所有的介面卡都是使用在中的 vsshlids 檔案中定義的 Guid 來建立。Visual Studio SDK 安裝的 \VisualStudioIntegration\Common\Inc\ 資料夾。 若要建立 VsTextBufferAdapter 的實例，請使用下列程式碼。  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>在 Managed 程式碼中建立介面卡  
 在 managed 程式碼中，您可以用與非受控碼所述的相同方式來建立介面卡。 您也可以使用 MEF 服務，讓您建立和與介面卡互動。 這種取得介面卡的方式，可讓您在共同建立介面卡時進行更細微的控制。  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>若要建立 IVsTextView 的介面卡  
  
1. 新增 Microsoft.VisualStudio.Editor.dll 的參考。 請確定 `CopyLocal` 已設為 `false`。  
  
2. 具現化，如下所示 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 。  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. 呼叫 `CreateX()` 方法。  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>直接從非受控碼使用 Visual Studio 編輯器  
 VisualStudio 命名空間和 VisualStudio. VSEditor 命名空間會將 COM 可呼叫介面公開為 IVx * 介面。 例如，VisualStudio 介面是介面的 COM 版本，而 IVxTextBuffer 介面則是 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 。 `IVxTextBuffer`您可以從取得緩衝區快照集的存取權、修改緩衝區、接聽緩衝區上的文字變更事件，以及建立追蹤點與範圍。 下列步驟示範如何 `IVxTextBuffer` 從存取 `IVsTextBuffer` 。  
  
#### <a name="to-get-an-ivxtextbuffer"></a>取得 IVxTextBuffer  
  
1. IVx * 介面的定義位於的 VSEditor .h 檔案中。Visual Studio SDK 安裝的 \VisualStudioIntegration\Common\Inc\ 資料夾。  
  
2. 下列程式碼會使用方法來具現化文字緩衝區 `IVsUserData->GetData()` 。 在下列程式碼中， `pData` 是物件的指標 `IVsUserData` 。  
  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>在非 MEF 元件中使用 Visual Studio 編輯器服務  
 如果您有不使用 MEF 的現有 managed 程式碼元件，而您想要使用 Visual Studio 編輯器的服務，您必須將參考加入包含 ComponentModelHost VSPackage 的元件，並取得其 SComponentModel 服務。  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>使用非 MEF 元件的 Visual Studio 編輯器元件  
  
1. 在中加入 Microsoft.VisualStudio.ComponentModelHost.dll 元件的參考。Visual Studio 安裝的 \Common7\IDE\ 資料夾。 請確定 `CopyLocal` 已設為 `false`。  
  
2. 將私 `IComponentModel` 用成員新增至您要在其中使用 Visual Studio 編輯器服務的類別，如下所示。  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. 在元件的初始化方法中具現化元件模型。  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. 之後，您可以呼叫所需服務的方法，以取得任何 Visual Studio 編輯器服務 `IComponentModel.GetService<T>()` 。  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```

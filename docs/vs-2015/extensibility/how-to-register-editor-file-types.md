---
title: 如何：註冊編輯器檔案類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204124"
---
# <a name="how-to-register-editor-file-types"></a>如何：註冊編輯器檔案類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

註冊編輯器檔案類型最簡單的方式，就是使用受控封裝架構中提供的註冊屬性 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] (MPF) 類別。 如果您是在原生中執行封裝 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] ，您也可以撰寫登入指令檔來註冊您的編輯器和相關聯的擴充功能。  
  
## <a name="registration-using-mpf-classes"></a>使用 MPF 類別註冊  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>若要使用 MPF 類別註冊編輯器檔案類型  
  
1. <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>在 VSPackage 的類別中，為您的編輯器提供適當參數的類別。  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Where」。Sample "是為此編輯器註冊的擴充功能，而" 32 "是其優先權層級。  
  
     `projectGuid`是中定義的其他檔案類型的 GUID <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> 。 提供其他檔案類型，因此產生的檔案不會成為組建程式的一部分。  
  
     `TemplateDir` 代表包含 managed basic 編輯器範例所附範本檔的資料夾。  
  
     `NameResourceID` 定義于 BasicEditorUI 專案的 Resources .h 檔案中，並將編輯器識別為「我的編輯器」。  
  
2. 覆寫 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
     在方法的執行中 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> ，呼叫 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> 方法並傳遞編輯器 factory 的實例，如下所示。  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     此步驟會註冊編輯器 factory 和編輯器副檔名。  
  
3. 取消註冊編輯器 factory。  
  
     當處置 VSPackage 時，會自動取消註冊編輯器 factory。 如果編輯器 factory 物件會實作為 <xref:System.IDisposable> 介面， `Dispose` 則會在將處理站取消註冊之後，呼叫其方法 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
## <a name="registration-using-a-registry-script"></a>使用登入指令檔進行註冊  
 使用登入指令檔來寫入 windows 登錄，以原生方式註冊 editor factory 和檔案類型 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] ，如下所示。  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>使用登入指令檔註冊編輯器檔案類型  
  
1. 在您的登入指令檔中，定義編輯器 factory 和 editor factory GUID 字串，如下列登錄 `GUID_BscEditorFactory` 腳本中的一節所示。 此外，也請定義編輯器延伸模組的延伸模組和優先順序：  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     此範例中的編輯器副檔名會識別為 ".rtf"，而其優先順序為 "50"。 GUID 字串定義于 BscEdit 範例專案的資源 .h 檔案中。  
  
2. 註冊 VSPackage。  
  
3. 註冊編輯器 factory。  
  
     編輯器 factory 已在執行中註冊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 。  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     GUID 字串是在 BscEdit 專案的資源 .h 檔案中定義。

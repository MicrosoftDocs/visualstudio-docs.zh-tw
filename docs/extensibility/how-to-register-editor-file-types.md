---
title: "如何： 註冊編輯器檔案類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9f2837dff6c5dd62c03da2ab340fca287a1da56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-register-editor-file-types"></a>如何： 註冊編輯器檔案類型
登錄編輯程式檔案類型的最簡單方式是使用屬性的一部分提供的登錄屬性[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]managed 封裝架構 (MPF) 類別。 如果您要實作您的封裝原生[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]，您也可以寫入登錄指令碼會註冊您的編輯器和相關聯的延伸模組。  
  
## <a name="registration-using-mpf-classes"></a>註冊使用 MPF 類別  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>若要註冊使用 MPF 類別編輯器檔案類型  
  
1.  提供<xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>以適當的參數編輯器 VSPackage 的類別中的類別。  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     其中"。範例 」 是此編輯器中，針對已註冊的延伸模組，且"32"其優先權層級。  
  
     `projectGuid`中定義的其他檔案類型的 guid <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>。 提供的其他檔案類型，如此所產生的檔案不在建置程序的一部分。  
  
     `TemplateDir`表示包含隨附於受管理的基本編輯器範例的範本檔案的資料夾。  
  
     `NameResourceID`定義於 Resources.h BasicEditorUI 專案檔，並找出以"My Editor"編輯器。  
  
2.  覆寫 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
     在您實作<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法，請呼叫<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>方法，然後傳遞做為您的編輯器 factory 的執行個體，則以下所示。  
  
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
  
     此步驟中登錄 editor factory 和編輯器的副檔名。  
  
3.  取消登錄編輯器 factory。  
  
     處置 VSPackage 時，會自動解除登錄編輯器 factory。 如果編輯器 factory 物件實作<xref:System.IDisposable>介面，其`Dispose`方法呼叫之後處理站已移除註冊使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="registration-using-a-registry-script"></a>使用登錄指令碼的註冊  
 登錄 editor factory 與檔案類型，原生[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]完成寫入 windows 登錄中，使用登錄指令碼，如下列所示。  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>若要註冊使用登錄指令碼編輯器的檔案類型  
  
1.  登錄指令碼中定義編輯器 factory 及編輯器 factory 的 GUID 字串中所示`GUID_BscEditorFactory`下列登錄指令碼區段。 此外，定義延伸模組和編輯器延伸模組的優先順序：  
  
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
  
     編輯器檔案延伸模組在此範例中被視為 「.rtf"，且 「 50"其優先權。 BscEdit 範例專案的 Resource.h 檔案中定義的 GUID 字串。  
  
2.  將 VSPackage 登錄。  
  
3.  登錄 editor factory。  
  
     在登錄編輯器 factory<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>實作。  
  
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
  
     BscEdit 專案的 Resource.h 檔案中定義的 GUID 字串。
---
title: HOW TO：登錄編輯程式檔案類型 |Microsoft Docs
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
ms.openlocfilehash: 697565600ef37024abde3acd8f2092c690f31e32
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945741"
---
# <a name="how-to-register-editor-file-types"></a>HOW TO：登錄編輯程式檔案類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

登錄編輯程式檔案類型的最簡單方式是使用隨附的登錄屬性[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]managed 封裝架構 (MPF) 類別。 如果您要實作您的套件，以原生[!INCLUDE[vcprvc](../includes/vcprvc-md.md)]，您也可以撰寫會註冊您的編輯器和相關聯的延伸模組的登錄指令碼。  
  
## <a name="registration-using-mpf-classes"></a>註冊使用 MPF 類別  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>若要登錄編輯程式檔案類型，使用 MPF 類別  
  
1.  提供<xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>以適當的參數，讓您的編輯器，VSPackage 的類別中的類別。  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     其中"。範例 」 是此編輯器中，已註冊的延伸模組和"32"是它的優先順序等級。  
  
     `projectGuid`中定義的其他檔案類型的 guid <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>。 提供的其他檔案類型，以便所產生的檔案不會在建置程序的一部分。  
  
     `TemplateDir` 表示包含隨附於受管理的基本編輯器範例的範本檔案的資料夾。  
  
     `NameResourceID` 定義於 Resources.h BasicEditorUI 專案檔案，並識別為 「 My 編輯器 」 編輯器。  
  
2.  覆寫 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
     在您實作<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法中，呼叫<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>方法並傳遞做為編輯器 factory 的執行個體，則以下所示。  
  
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
  
     此步驟中註冊編輯器 factory 及編輯器的副檔名。  
  
3.  取消登錄編輯器 factory。  
  
     處置 VSPackage 時，會自動解除登錄編輯器 factory。 如果編輯器 factory 物件會實作<xref:System.IDisposable>介面，其`Dispose`方法呼叫之後的處理站已移除註冊使用[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
## <a name="registration-using-a-registry-script"></a>使用登錄指令碼的註冊  
 在原生註冊 editor factory 與檔案類型[!INCLUDE[vcprvc](../includes/vcprvc-md.md)]完成寫入 windows 登錄中，使用登錄指令碼，如下列所示。  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>若要註冊使用登錄指令碼編輯器的檔案類型  
  
1.  在您登錄指令碼中，定義編輯器 factory 及編輯器 factory 的 GUID 字串中所示`GUID_BscEditorFactory`下列登錄指令碼區段。 此外，定義延伸模組及編輯器擴充功能的優先權：  
  
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
  
     編輯器檔案延伸模組，在此範例會識別為 「.rtf"，其優先順序是"50"。 BscEdit 範例專案的 Resource.h 檔案中定義的 GUID 字串。  
  
2.  註冊 VSPackage。  
  
3.  登錄編輯器 factory。  
  
     編輯器 factory 會在中註冊<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>實作。  
  
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
  
     BscEdit 專案 Resource.h 檔案中定義的 GUID 字串。

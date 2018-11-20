---
title: 註冊舊版語言服務 1 |Microsoft Docs
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
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e473df78787b83655c402bae666448e718216b36
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769601"
---
# <a name="registering-a-legacy-language-service"></a>註冊舊版語言服務
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage 在 managed 的 package framework (MPF) 提供的語言服務 (請參閱[Vspackage](../../extensibility/internals/vspackages.md)) 並已向[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]藉由新增登錄機碼和項目。 此登錄程序是在部分是在安裝期間，有一部分是在執行階段中完成。  
  
## <a name="register-the-language-service-by-using-attributes"></a>使用屬性來註冊語言服務  
 下列屬性用來註冊語言服務。  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>  
  
  以下將說明這些屬性  
  
### <a name="provideserviceattribute"></a>ProvideServiceAttribute  
 這個屬性做為服務註冊您的語言服務。  
  
### <a name="example"></a>範例  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideServiceAttribute(typeof(TestLanguageService),  
                             ServiceName = "Test Language Service")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute  
 這個屬性特別為語言服務註冊您的語言服務。 它可讓您設定的選項，指定您的語言服務提供的功能。 此範例顯示語言服務可以提供的選項的子集。 完整的語言服務選項集，請參閱<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。  
  
### <a name="example"></a>範例  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),  
                             "Test Language",  
                             106,             // resource ID of localized language name  
                             CodeSense = true,             // Supports IntelliSense  
                             RequestStockColors = false,   // Supplies custom colors  
                             EnableCommenting = true,      // Supports commenting out code  
                             EnableAsyncCompletion = true  // Supports background parsing  
                             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute  
 這個屬性會將您的語言服務關聯副檔名的檔案。 只要載入該副檔名的檔案時，在任何專案中，語言服務會啟動，而且用來顯示檔案的內容。  
  
### <a name="example"></a>範例  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),  
                                       ".Testext")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute  
 這個屬性會註冊從哪一個程式碼的擴充，或者程式碼片段範本所取得的位置。 這項資訊由**程式碼片段瀏覽器**和編輯器的程式碼片段插入至原始程式檔時。  
  
### <a name="example"></a>範例  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageCodeExpansionAttribute(  
             typeof(TestLanguageService),  
             "Test Language", // Name of language used as registry key.  
             106,           // Resource ID of localized name of language service.  
             "testlanguage",  // language key used in snippet templates.  
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index  
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +  
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute  
 這個屬性會註冊屬性頁中顯示**選項**下方的對話方塊**文字編輯器**類別目錄。 使用其中一個屬性，為每個頁面會顯示為您的語言服務。 如果您需要組織頁面樹狀結構中的，使用其他屬性來定義每個節點的樹狀結構。  
  
### <a name="example"></a>範例  
 此範例示範兩個屬性頁中，**選項**並**Indenting**，和一個節點，其中包含第二個屬性頁。  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Options",      // Registry key name for property page  
             "#242",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Advanced",     // Registry key name for node  
             "#243",         // Localized name of node  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             @"Advanced\Indenting",     // Registry key name for property page  
             "#244",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
## <a name="proffer-the-language-service-at-runtime"></a>Proffer 語言服務，在執行階段  
 載入您的語言套件時，您必須告訴[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，已可供您的語言服務。 您可以 proffering 服務。 這在完成<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。 此外，您需要啟動計時器，在閒置期間呼叫您的語言服務，因此可以完成背景剖析。 此閒置計時器也會用來更新文件屬性，如果您已實作任何透過<xref:Microsoft.VisualStudio.Package.DocumentProperties>類別。 為了支援計時器，必須實作您的套件<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent>介面 (只有<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A>方法需要完全實作; 其餘的方法可以傳回預設值)。  
  
### <a name="example"></a>範例  
 這個範例示範 proffering 服務，並提供，閒置計時器的典型方法。  
  
```csharp  
  
using System;  
using System.Runtime.InteropServices;  
using System.ComponentModel.Design;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.OLE.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,  
        AutoOutlining = true,  
        EnableCommenting = true,  
        MatchBraces = true,  
        ShowMatchingBrace = true)]  
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package  
  
    public class TestLanguagePackage : Package, IOleComponent  
    {  
        private uint m_componentID;  
  
        protected override void Initialize()  
        {  
            base.Initialize();  // required  
  
            // Proffer the service.  
            IServiceContainer serviceContainer = this as IServiceContainer;  
            TestLanguageService langService      = new TestLanguageService();  
            langService.SetSite(this);  
            serviceContainer.AddService(typeof(TestLanguageService),  
                                        langService,  
                                        true);  
  
            // Register a timer to call our language service during  
            // idle periods.  
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                       as IOleComponentManager;  
            if (m_componentID == 0 && mgr != null)  
            {  
                OLECRINFO[] crinfo = new OLECRINFO[1];  
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));  
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |  
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;  
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal     |  
                                              (uint)_OLECADVF.olecadvfRedrawOff |  
                                              (uint)_OLECADVF.olecadvfWarningsOff;  
                crinfo[0].uIdleTimeInterval = 1000;  
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);  
            }  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (m_componentID != 0)  
            {  
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                           as IOleComponentManager;  
                if (mgr != null)  
                {  
                    int hr = mgr.FRevokeComponent(m_componentID);  
                }  
                m_componentID = 0;  
            }  
  
            base.Dispose(disposing);  
        }  
  
        #region IOleComponent Members  
  
        public int FDoIdle(uint grfidlef)  
        {  
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;  
            // Use typeof(TestLanguageService) because we need to  
            // reference the GUID for our language service.  
            LanguageService service = GetService(typeof(TestLanguageService))  
                                      as LanguageService;  
            if (service != null)  
            {  
                service.OnIdle(bPeriodic);  
            }  
            return 0;  
        }  
  
        public int FContinueMessageLoop(uint uReason,  
                                        IntPtr pvLoopData,  
                                        MSG[] pMsgPeeked)  
        {  
            return 1;  
        }  
  
        public int FPreTranslateMessage(MSG[] pMsg)  
        {  
            return 0;  
        }  
  
        public int FQueryTerminate(int fPromptUser)  
        {  
            return 1;  
        }  
  
        public int FReserved1(uint dwReserved,  
                              uint message,  
                              IntPtr wParam,  
                              IntPtr lParam)  
        {  
            return 1;  
        }  
  
        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)  
        {  
            return IntPtr.Zero;  
        }  
  
        public void OnActivationChange(IOleComponent pic,  
                                       int fSameComponent,  
                                       OLECRINFO[] pcrinfo,  
                                       int fHostIsActivating,  
                                       OLECHOSTINFO[] pchostinfo,  
                                       uint dwReserved)  
        {  
        }  
  
        public void OnAppActivate(int fActive, uint dwOtherThreadID)  
        {  
        }  
  
        public void OnEnterState(uint uStateID, int fEnter)  
        {  
        }  
  
        public void OnLoseActivation()  
        {  
        }  
  
        public void Terminate()  
        {  
        }  
  
        #endregion  
    }  
}   
```


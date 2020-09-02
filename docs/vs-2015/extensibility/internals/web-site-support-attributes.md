---
title: 網站支援屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144302"
---
# <a name="web-site-support-attributes"></a>網站支援屬性
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 您可以擴充網站專案，以提供 Web 程式設計語言的支援。 語言必須自行註冊， [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 以便在選取語言時，專案範本可以出現在 [ **新網站** ] 對話方塊中。  
  
 IronPython Studio 範例包含網站支援。 您可以使用 [VSSDK 範例](../../misc/vssdk-samples.md)來尋找它。 它包含下列屬性類別，可將 IronPython 註冊為新 Web 專案的程式碼後置語言。  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 這個屬性會置於語言專案上。 它會將語言新增至 [**新網站**] 對話方塊之 [**語言**] 清單中的 Web 程式設計語言清單。 例如，下列程式會將 IronPython 新增至清單：  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 這個屬性也會設定範本路徑以指向 [範本] 資料夾。 如需 [範本] 資料夾位置的詳細資訊，請參閱 [網站支援範本](../../extensibility/internals/web-site-support-templates.md)。  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 這個屬性會置於語言專案上。 它可讓網站專案在 **方案總管**中 (主要) 的另一個檔案類型下，將一種檔案類型 (相關的) 。  
  
 例如：  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 指定 IronPython 程式碼後置檔案與 .aspx 檔案相關。 在 IronPython 網站方案中建立新的 .aspx 網頁時，會產生新的 .py 原始程式檔，並顯示為 .aspx 頁面的子節點。  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 這個屬性會置於語言專案封裝中。 它會選取語言的 Intellisense 提供者。  
  
 例如：  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 指定應視需要建立 PythonIntellisenseProvider 的實例， <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> 以提供語言服務。  
  
 當要求包含程式碼但未快取的網頁時，IVsIntellisenseProject 執行會處理參考並呼叫語言編譯器。  
  
## <a name="see-also"></a>另請參閱  
 [網站支援](../../extensibility/internals/web-site-support.md)

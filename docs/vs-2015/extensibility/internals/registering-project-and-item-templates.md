---
title: 註冊專案和項目範本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a06e7a292d960e675ad4b0de97499557542fef1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185842"
---
# <a name="registering-project-and-item-templates"></a>註冊專案和項目範本
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

專案類型都必須註冊其專案和專案項目範本的所在位置的目錄。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 使用您的專案類型相關聯的註冊資訊來判斷要顯示在**加入新的專案**並**加入新項目**對話方塊。  
  
 如需有關範本的詳細資訊，請參閱 <<c0> [ 加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
## <a name="registry-entries-for-projects"></a>專案的登錄項目  
 下列範例會示範 hkey_local_machine\software\microsoft\visualstudio \ 底下的登錄項目\\<*版本*>。 隨附的表格會說明範例中使用的項目。  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|@|REG_SZ|這種專案的預設名稱。|  
|DisplayName|REG_SZ|要從附屬 DLL 擷取的資源識別碼名稱的註冊套件。|  
|套件|REG_SZ|註冊套件的套件的類別識別碼。|  
|ProjectTemplatesDir|REG_SZ|預設的專案範本檔案的路徑。 專案範本檔案會顯示**新的專案**範本。|  
  
### <a name="registering-item-templates"></a>註冊項目範本  
 您必須註冊您在其中儲存項目範本的目錄。  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|名稱|類型|說明|  
|----------|----------|-----------------|  
|@|REG_SZ|加入項目範本的資源識別碼。|  
|TemplatesDir|REG_SZ|在對話方塊中顯示的專案項目路徑**加入新項目**精靈。|  
|TemplatesLocalizedSubDir|REG_SZ|資源識別碼的字串，可命名的子目錄 TemplatesDir 保存當地語系化的範本。 因為[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]載入字串資源的附屬 Dll 如果有的話，每個附屬 DLL 可以包含不同的當地語系化的子目錄的名稱。|  
|SortPriority|REG_DWORD|設定控管中顯示範本的順序 SortPriority**加入新項目** 對話方塊。 稍早在 [範本] 清單中，會出現較大的 SortPriority 值。|  
  
### <a name="registering-file-filters"></a>註冊檔案篩選器  
 （選擇性） 您可以在其中註冊篩選條件，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]時檔案名稱，它會提示使用。 例如，[!INCLUDE[csprcs](../../includes/csprcs-md.md)]篩選**開啟檔案**對話方塊：  
  
 **Visual C# 檔案 (\*.cs\*.resx\*.settings，\*.xsd，\*.wsdl);\*。cs\*.resx\*.settings，\*.xsd，\*.wsdl)**  
  
 若要支援註冊多個篩選器，每個篩選條件會在自己 hkey_local_machine\software\microsoft\visualstudio \ 底下的子機碼中註冊\\<*版本*> \Projects\\{\< *ProjectGUID*>} \Filters\\<*子機碼*>。 子機碼的名稱是任意的。[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]會忽略子機碼的名稱，並使用只是它的值。  
  
 您可以控制在其中一個篩選器由設定旗標下, 表所示的內容。 如果篩選器沒有設定任何旗標，它會列出中常見的篩選後**加入現有項目** 對話方塊中，**開啟檔案** 對話方塊中，但它不會使用在**檔案中尋找**  對話方塊。  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|可在其中一個常見的篩選器的篩選**檔案中尋找** 對話方塊。 常見的篩選條件會列出未標示為常見的篩選條件之前篩選清單中。|  
|CommonOpenFilesFilter|REG_DWORD|可在其中一個常見的篩選器的篩選**開啟檔案** 對話方塊。 常見的篩選條件會列出未標示為常見的篩選條件之前篩選清單中。|  
|FindInFilesFilter|REG_DWORD|列出篩選器中的常見篩選器之後**檔案中尋找** 對話方塊。|  
|NotOpenFileFilter|REG_DWORD|表示在不使用篩選條件**開啟檔案** 對話方塊。|  
|NotAddExistingItemFilter|REG_DWORD|表示在不使用篩選條件**加入現有項目** 對話方塊。|  
|SortPriority|REG_DWORD|設定 SortPriority 控管的篩選會顯示的順序。 稍早在篩選清單中，會出現較大的 SortPriority 值。|  
  
## <a name="directory-structure"></a>目錄結構  
 Vspackage 可以將放範本檔案和資料夾任何地方在本機或遠端磁碟上，只要透過整合式的開發環境 (IDE) 註冊的位置。 不過，為了方便組織，我們建議在您的產品安裝路徑下的下列目錄結構。  
  
 \Templates  
  
 \Projects （包含專案範本）  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems （包含專案項目）  
  
 \Class  
  
 \Form  
  
 \Web 頁面  
  
 \HelperFiles （包含多個檔案的專案項目中使用的檔案）  
  
 \WizardFiles  
  
## <a name="see-also"></a>另請參閱  
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [當地語系化應用程式](../../ide/localizing-applications.md)   
 [通常用來擴充專案的物件 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

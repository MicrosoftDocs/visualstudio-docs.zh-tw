---
title: 註冊專案和專案範本 |Microsoft Docs
description: 瞭解 Visual Studio 如何針對您的專案類型使用註冊資訊，以判斷要在 [加入新專案] 和 [加入新專案] 對話方塊中顯示的內容。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc268236a10ab3f6be660b0e69a82a8f656f8910
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837236"
---
# <a name="registering-project-and-item-templates"></a>註冊專案和項目範本
專案類型必須註冊其專案和專案專案範本所在的目錄。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用與您的專案類型相關聯的註冊資訊，來決定要在 [ **加入新專案** ] 和 [ **加入新** 專案] 對話方塊中顯示的內容。

 如需範本的詳細資訊，請參閱 [加入專案和專案專案範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。

## <a name="registry-entries-for-projects"></a>專案的登錄專案
 下列範例會顯示 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *版本*> 下的登錄專案。 隨附的表格說明範例中使用的元素。

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|名稱|類型|Description|
|----------|----------|-----------------|
|@|REG_SZ|這種專案的預設名稱。|
|DisplayName|REG_SZ|要從在封裝下註冊的附屬 DLL 中取出之名稱的資源識別碼。|
|套件|REG_SZ|封裝下註冊之封裝的類別識別碼。|
|ProjectTemplatesDir|REG_SZ|專案範本檔案的預設路徑。 **新的專案** 範本會顯示專案範本檔案。|

### <a name="registering-item-templates"></a>註冊專案範本
 您必須註冊儲存專案範本的目錄。

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| 名稱 | 類型 | Description |
|--------------------------|-----------| - |
| @ | REG_SZ | 新增專案範本的資源識別碼。 |
| TemplatesDir | REG_SZ | 在 [ **加入新專案** ] 嚮導的對話方塊中顯示之專案專案的路徑。 |
| TemplatesLocalizedSubDir | REG_SZ | 字串的資源識別碼，該字串會命名保存當地語系化範本的 TemplatesDir 子目錄。 因為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 從附屬 dll 載入字串資源（如果有的話），所以每個附屬 dll 都可以包含不同的當地語系化子目錄名稱。 |
| SortPriority | REG_DWORD | 設定 SortPriority，以管理範本在 [ **加入新專案** ] 對話方塊中的顯示順序。 較大的 SortPriority 值會出現在範本清單中。 |

### <a name="registering-file-filters"></a>註冊檔案篩選
 （選擇性）您可以 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在提示輸入檔案名時，註冊使用的篩選準則。 例如，[ [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] **開啟** 檔案] 對話方塊的篩選準則為：

 **Visual c # 檔案 (\* .cs、 \* .resx、 \* . settings、 \* .xsd、 \* .wsdl) ; \* 。cs、 \* .resx、 \* . settings、 \* .xsd、 \* .wsdl)**

 為了支援註冊多個篩選，每個篩選器會在 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *版本*> \projects \\ { \<*ProjectGUID*> } \Filters \\ < 子機碼> 的子機碼中註冊。 子機碼名稱為任意;忽略子機碼 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的名稱，並只使用其值。

 您可以藉由設定旗標（如下表所示）來控制用來篩選篩選器的內容。 如果篩選沒有設定任何旗標，則會在 [ **加入現有專案** ] 對話方塊和 [ **開啟** 檔案] 對話方塊中的一般篩選準則之後列出，但不會在 [檔案中 **尋找** ] 對話方塊中使用。

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

|名稱|類型|Description|
|----------|----------|-----------------|
|CommonFindFilesFilter|REG_DWORD|在 [檔案 **中尋找** ] 對話方塊中，篩選出其中一個常見的篩選準則。 一般篩選準則會在篩選器清單中列出，然後才會將篩選標記為通用。|
|CommonOpenFilesFilter|REG_DWORD|在 [ **開啟** 檔案] 對話方塊中，讓篩選準則成為其中一個常見的篩選準則。 一般篩選準則會在篩選器清單中列出，然後才會將篩選標記為通用。|
|FindInFilesFilter|REG_DWORD|在 [檔案 **中尋找** ] 對話方塊中的一般篩選準則之後列出篩選。|
|NotOpenFileFilter|REG_DWORD|指出篩選不會在 [ **開啟** 檔案] 對話方塊中使用。|
|NotAddExistingItemFilter|REG_DWORD|指出篩選不會在 [ **加入現有專案** ] 對話方塊中使用。|
|SortPriority|REG_DWORD|設定 SortPriority 以管理篩選器的顯示順序。 較大的 SortPriority 值會稍早出現在篩選清單中。|

## <a name="directory-structure"></a>目錄結構
 只要透過整合式開發環境 (IDE) 註冊位置，Vspackage 可以將範本檔案和資料夾放在本機或遠端磁片上的任何位置。 不過，為了方便組織，建議您在產品的安裝路徑底下採用下列目錄結構。

 \Templates

 \Projects (包含專案範本) 

 \Applications and

 \Components

 \ ...

 \ProjectItems (包含專案專案) 

 \Class

 \Form

 \Web 頁面

 \HelperFiles (包含多檔案專案專案中所使用的檔案) 

 \WizardFiles

## <a name="see-also"></a>另請參閱

- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [精靈](../../extensibility/internals/wizards.md)
- [當地語系化應用程式](../../ide/globalizing-and-localizing-applications.md)
- [通常用來擴充專案的物件 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

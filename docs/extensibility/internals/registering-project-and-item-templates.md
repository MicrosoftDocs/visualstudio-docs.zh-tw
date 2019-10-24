---
title: 註冊專案和專案範本 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e35a476ab8fe8d8de3ce11dd117de4c84a3befa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724633"
---
# <a name="registering-project-and-item-templates"></a>註冊專案和項目範本
專案類型必須註冊其專案和專案專案範本所在的目錄。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會使用與您的專案類型相關聯的註冊資訊，來決定要在 [**加入新專案**] 和 [**加入新專案**] 對話方塊中顯示的內容。

 如需範本的詳細資訊，請參閱[加入專案和專案專案範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。

## <a name="registry-entries-for-projects"></a>專案的登錄專案
 下列範例會顯示 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*版本*> 下的登錄專案。 隨附的資料表說明範例中使用的元素。

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|[屬性]|輸入|描述|
|----------|----------|-----------------|
|@|REG_SZ|這種專案的預設名稱。|
|DisplayName|REG_SZ|要從在封裝下註冊的附屬 DLL 中抓取之名稱的資源識別碼。|
|封裝|REG_SZ|封裝下註冊之套件的類別識別碼。|
|ProjectTemplatesDir|REG_SZ|專案範本檔案的預設路徑。 [**新增專案**] 範本會顯示專案範本檔案。|

### <a name="registering-item-templates"></a>註冊專案範本
 您必須註冊用來儲存專案範本的目錄。

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| [屬性] | 輸入 | 描述 |
|--------------------------|-----------| - |
| @ | REG_SZ | 新增專案範本的資源識別碼。 |
| TemplatesDir | REG_SZ | [**加入新專案**] wizard 的對話方塊中所顯示專案專案的路徑。 |
| TemplatesLocalizedSubDir | REG_SZ | 字串的資源識別碼，其名稱為保存當地語系化範本的 TemplatesDir 子目錄。 因為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會從附屬 Dll 載入字串資源（如果有的話），每個附屬 DLL 都可以包含不同的當地語系化子目錄名稱。 |
| SortPriority | REG_DWORD | 設定 SortPriority，以管理範本在 [**加入新專案**] 對話方塊中的顯示順序。 較大的 SortPriority 值較早出現在範本清單中。 |

### <a name="registering-file-filters"></a>註冊檔案篩選
 （選擇性）您可以在提示輸入檔案名時，註冊 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用的篩選準則。 例如，[**開啟**檔案] 對話方塊的 [[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 篩選] 是：

 **視覺C#效果檔案（\* .cs、\* .resx、\* 設定、\*、\* .wsdl）;\* .cs、\* .resx、\* 設定、0、1 .wsdl）**

 為了支援註冊多個篩選準則，每個篩選器都會在 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*版本*> \Projects \\ {\<*ProjectGUID*>} \Filters 的其自有子機碼中註冊\\ <*子*機碼 >。 子機碼名稱是任意的; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會忽略子機碼的名稱，並只使用其值。

 您可以藉由設定旗標來控制用來篩選的內容，如下表所示。 如果篩選器未設定任何旗標，則會在 [**加入現有專案**] 對話方塊和 [**開啟**檔案] 對話方塊中的通用篩選後列出，但不會用於 [檔案中**尋找**] 對話方塊。

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

|[屬性]|輸入|描述|
|----------|----------|-----------------|
|CommonFindFilesFilter|REG_DWORD|讓篩選準則成為 [檔案**中尋找**] 對話方塊中的其中一個通用篩選準則。 一般篩選準則會在篩選器清單中列出，然後篩選器才會標示為通用。|
|CommonOpenFilesFilter|REG_DWORD|讓篩選準則成為 [**開啟**檔案] 對話方塊中的其中一個通用篩選準則。 一般篩選準則會在篩選器清單中列出，然後篩選器才會標示為通用。|
|FindInFilesFilter|REG_DWORD|在 [檔案**中尋找**] 對話方塊中列出一般篩選器之後的篩選準則。|
|NotOpenFileFilter|REG_DWORD|表示篩選準則不會用於 [**開啟**檔案] 對話方塊中。|
|NotAddExistingItemFilter|REG_DWORD|表示篩選準則不會在 [**加入現有專案**] 對話方塊中使用。|
|SortPriority|REG_DWORD|設定 SortPriority 以管理篩選器的顯示順序。 較大的 SortPriority 值會在較早的篩選清單中出現。|

## <a name="directory-structure"></a>目錄結構
 Vspackage 可以將範本檔案和資料夾放在本機或遠端磁片上的任何位置，只要該位置是透過整合式開發環境（IDE）註冊即可。 不過，為了方便組織，我們建議您在產品的安裝路徑底下採用下列目錄結構。

 \Templates

 \Projects （包含專案範本）

 \Applications and

 \Components

 \ ...

 \ProjectItems （包含專案專案）

 \Class

 \Form

 \Web 頁面

 \HelperFiles （包含多檔案專案專案中所使用的檔案）

 \WizardFiles

## <a name="see-also"></a>請參閱

- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [精靈](../../extensibility/internals/wizards.md)
- [當地語系化應用程式](../../ide/globalizing-and-localizing-applications.md)
- [通常用來擴充專案的物件 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
---
title: 註冊項目和項目範本 |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705816"
---
# <a name="registering-project-and-item-templates"></a>註冊專案和項目範本
專案類型必須註冊其專案和專案專案範本所在的目錄。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用與項目類型關聯的註冊資訊來確定要在 **「添加新專案和****添加新項目**」對話框中顯示的內容。

 有關範本的詳細資訊,請參閱[新增專案和專案專案範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。

## <a name="registry-entries-for-projects"></a>專案的註冊表項
 以下範例顯示HKEY_LOCAL_MACHINE\軟體\微軟_VisualStudio\\<*版本*>下的注册表项。 隨附的表說明瞭示例中使用的元素。

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|名稱|類型|描述|
|----------|----------|-----------------|
|@|REG_SZ|此類項目的預設名稱。|
|DisplayName|REG_SZ|要從在「包」下註冊的衛星 DLL 檢索的名稱的資源 ID。|
|Package|REG_SZ|在「包」下註冊的包的類 ID。|
|專案樣本Dir|REG_SZ|專案範本檔的預設路徑。 專案範本檔由**新專案**樣本顯示。|

### <a name="registering-item-templates"></a>註冊項目範本
 您必須註冊存儲專案範本的目錄。

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| 名稱 | 類型 | 描述 |
|--------------------------|-----------| - |
| @ | REG_SZ | 添加專案範本的資源 ID。 |
| 範本迪爾 | REG_SZ | **"添加新專案**"嚮導的對話框中顯示的專案項的路徑。 |
| 樣本本地化子 Dir | REG_SZ | 命名儲存本地化範本的 TemplatesDir 子目錄的字串的資源 ID。 由於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如果具有附屬 DLL,則從附屬 DLL 載入字串資源,因此每個附屬 DLL 可以包含不同的當地語系化子目錄名稱。 |
| 排序優先權 | REG_DWORD | 設置排序優先順序以控制範本在「**新增新項目**」對話框中的顯示順序。 較大的排序優先順序值出現在範本清單中的較早位置。 |

### <a name="registering-file-filters"></a>註冊檔案篩選器
 或者,您可以註冊在提示檔名時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用的篩選器。 例如,「[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]**開啟檔案」** 對話框的篩選器是:

 **可\*視化 C# 檔(.cs、.resx、.\*\*設置、.xsd、.wsdl);\* \*\*.cs,\*\*.resx,\*. 設置,\*.xsd, .wsdl)**

 為了支援多個篩選器的註冊,每個\\<篩選器在HKEY_LOCAL_MACHINE\軟體\Microsoft_VisualStudio*Version*版本\\\<>_项目 [*ProjectGUID*>]\\<下>"下註冊自己的子*鍵*。 子鍵名稱是任意的;[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]忽略子鍵的名稱,只使用其值。

 您可以通過設定標記來控制使用篩選器的上下文,如下表所示。 如果篩選器未設定任何標誌,它將在「**新增現有項目**」對話框和 **「打開檔案」** 對話框中的常用篩選器之後列出,但不會在「**在檔案中搜尋**」對話框中使用。

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
|常見搜尋檔案篩選器|REG_DWORD|使篩選器成為「**在檔案中搜尋**」對話框中的常見篩選器之一。 在篩選器未標記為公共篩選器之前,篩選器將列在篩選器清單中。|
|常見開啟檔案篩選器|REG_DWORD|使篩選器成為 **「打開檔」** 對話框中常見的篩選器之一。 在篩選器未標記為公共篩選器之前,篩選器將列在篩選器清單中。|
|尋找檔案篩選器|REG_DWORD|在「**在檔案中搜尋**」對話框中列出常見篩選器後篩選器。|
|未開啟檔案篩選器|REG_DWORD|指示篩選器未在 **「打開檔」** 對話方塊中使用。|
|未新增現有項目篩選器|REG_DWORD|指示篩選器未在 **「添加現有項目」** 對話方塊中使用。|
|排序優先權|REG_DWORD|設置排序優先順序以控制篩選器的顯示順序。 較大的排序優先順序值出現在篩選器清單中的較早位置。|

## <a name="directory-structure"></a>目錄結構
 只要位置是通過整合式開發環境 (IDE) 註冊,VS 包就可以將範本檔和資料夾放在本地或遠端磁碟上的任意位置。 但是,為了便於組織,我們建議在產品的安裝路徑下採用以下目錄結構。

 *範本

 *專案(包含項目範本)

 *應用

 *元件

 \ ...

 *專案專案(包含項目 )

 *類別

 *表格

 *網頁

 • 協助檔案(包含多檔案項目項目中使用的檔案)

 *精靈檔案

## <a name="see-also"></a>另請參閱

- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [嚮導](../../extensibility/internals/wizards.md)
- [當地語系化應用程式](../../ide/globalizing-and-localizing-applications.md)
- [通常用來擴充專案的物件 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

---
title: 註冊專案類型 |Microsoft Docs
description: 瞭解如何建立登錄專案，讓 Visual Studio 辨識和使用您的新專案類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e54f62a90ece61fc2dd8f3cc2b242957f249ed33
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062768"
---
# <a name="registering-a-project-type"></a>註冊專案類型
當您建立新的專案類型時，您必須建立登錄專案，讓 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 能夠辨識和使用您的專案類型。 您通常會使用登入指令檔 ( .rgs) 檔案來建立這些登錄專案。

 在下列範例中，登錄中的語句會提供預設的路徑和資料（如果適用的話），後面接著包含每個語句的登入指令檔專案的資料表。 資料表會提供腳本專案和語句的其他相關資訊。

> [!NOTE]
> 下列登錄資訊的目的，是為了註冊您的專案類型而要寫入的登入指令檔中的專案類型和用途。 您的實際專案和其使用方式可能會根據您專案類型的特定需求而異。 您應查看可用的範例，找出與您正在開發的專案類型非常類似的範例，然後檢查該範例的登入指令檔。

 以下是來自 HKEY_CLASSES_ROOT 的範例。

## <a name="example-1"></a>範例 1

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|副檔名為 figp 之專案類型檔案的名稱和描述。|
|`Content Type`|REG_SZ|`Text/plain`|專案檔案的內容類型。|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|此類型的專案所使用的預設圖示。 % MODULE% 語句已在登錄中完成至專案類型 DLL 的預設位置。|
|`@`|REG_SZ|`&Open in Visual Studio`|將開啟此專案類型的預設應用程式。|
|`@`|REG_SZ|`devenv.exe "%1"`|當開啟此類型的專案時，將會執行的預設命令。|

 下列範例來自 HKEY_LOCAL_MACHINE，且位於登錄機碼 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] 底下。

## <a name="example-2"></a>範例 2

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`@` (預設值)|REG_SZ|`FigPrj Project VSPackage`|這個已註冊 VSPackage (專案類型) 的可當地語系化名稱。|
|`InprocServer32`|REG_SZ|`%MODULE%`|專案類型 DLL 的路徑。 IDE 會載入此 DLL，並將 VSPackage CLSID 傳遞給，以 `DllGetClassObject` 取得 <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> 以建立 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 物件。|
|`CompanyName`|REG_SZ|`Microsoft`|開發專案類型的公司名稱。|
|`ProductName`|REG_SZ|`Figure Project Sample`|專案類型的名稱。|
|`ProductVersion`|REG_SZ|`9.0`|專案類型版本的版本號碼。|
|`MinEdition`|REG_SZ|`professional`|註冊的 VSPackage 版本。|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|專案 VSPackage 的封裝載入機碼。 當專案在環境啟動後載入時，就會驗證金鑰。|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|附屬 DLL 的檔案名，其中包含專案類型的當地語系化資源。|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|附屬 DLL 的路徑。|
|`FigProjectsEvents`|REG_SZ|請參閱值的語句。|判斷針對這個 automation 事件傳回的文字字串。|
|`FigProjectItemsEvents`|REG_SZ|請參閱值的語句。|判斷針對這個 automation 事件傳回的文字字串。|

 下列所有範例都位於登錄機碼 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 下的登錄中。

## <a name="example-3"></a>範例 3

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|此類型之專案的預設名稱。|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|要從在封裝下註冊的附屬 DLL 中取出之名稱的資源識別碼。|
|`Package`|REG_SZ|`%CLSID_Package%`|封裝下註冊之 VSPackage 的類別識別碼。|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|專案範本檔案的預設路徑。 這些是新的專案範本所顯示的檔案。|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|專案專案範本檔案的預設路徑。 這些是 [加入新專案] 範本所顯示的檔案。|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|啟用 IDE 以執行 [ **開啟** ] 對話方塊。|
|`PossibleProjectExtensions`|REG_SZ|`figp`|由 IDE 用來判斷開啟的專案是否由這個專案類型 (project factory) 處理。 有多個專案的格式是以分號分隔的清單。 例如 "vdproj; vdp"。|
|`DefaultProjectExtension`|REG_SZ|`.figp`|供 IDE 用來作為 [另存新檔] 作業的預設副檔名。|
|`Filter Settings`|REG_DWORD|不同的，請參閱下表中的語句和批註。|這些設定是用來設定各種篩選器，以便在 UI 對話方塊中顯示檔案。|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|新增專案範本的資源識別碼。|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|在 [ **加入新專案** ] 範本的對話方塊中顯示之專案專案的路徑。|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|決定在 [ **加入新專案** ] 對話方塊中顯示之檔案的樹狀節點中的排序次序。|

 下表顯示先前程式碼區段中可用的篩選選項。

|篩選選項|Description|
|-------------------|-----------------|
|`CommonFindFilesFilter`|指出篩選是 [檔案 **中尋找** ] 對話方塊中的其中一個常見篩選準則。 一般篩選器會列在篩選器清單中，然後才會將篩選準則標示為 common。|
|`CommonOpenFilesFilter`|指出篩選是 [ **開啟** 檔案] 對話方塊中的其中一個常見的篩選準則。 一般篩選器會列在篩選器清單中，然後才會將篩選準則標示為 common。|
|`FindInFilesFilter`|指出篩選將是 [ **在檔案中尋找** ] 對話方塊中的其中一個篩選準則，而且會列在一般篩選準則之後。|
|`NotOpenFileFilter`|指出篩選不會在 [ **開啟** 檔案] 對話方塊中使用。|
|`NotAddExistingItemFilter`|指出篩選不會在 [加入 **現有專案** ] 對話方塊中使用。|

 依預設，如果某個篩選沒有設定其中一或多個旗標，則會在列出一般篩選器之後，在 [ **加入現有專案** ] 對話方塊和 [ **開啟** 檔案] 對話方塊中使用篩選。 篩選準則不會用在 [檔案 **中尋找** ] 對話方塊中。

 下列所有範例都位於登錄機碼 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 下的登錄中。

## <a name="example-4"></a>範例 4

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|新專案範本的資源識別碼。|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|已註冊專案類型專案的預設路徑。|
|`SortPriority`|REG_DWORD|`41 (x29)`|設定 [新增專案] 對話方塊中顯示之專案的排序次序。|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0表示此類型的專案只顯示在 [新增專案] 對話方塊中。|

 下列所有範例都位於登錄機碼 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 下的登錄中。

## <a name="example-5"></a>範例 5

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|無|預設值，表示下列專案適用于其他檔案專案專案。|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|[加入新專案] 範本檔案的資源識別碼值。|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|將在 [ **加入新專案** ] 對話方塊中顯示之專案的預設路徑。|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|在 [ **加入新專案** ] 對話方塊的樹狀節點中，建立顯示的排序次序。|

 下列範例位於登錄機碼 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] 下的登錄中。

## <a name="example-6"></a>範例 6

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 功能表項目會將 IDE 指向用來取出功能表資訊的資源。 當此資料合併到功能表資料庫時，將會在登錄的 MenusMerged 區段中新增相同的索引鍵。 VSPackage 不應該直接修改 MenusMerged 區段下的任何內容。 在下表的 [資料] 欄位中，有三個以逗號分隔的欄位。 第一個欄位會識別功能表資源檔的完整路徑：

- 如果省略第一個欄位，則會從 VSPackage GUID 所識別的附屬 DLL 載入功能表資源。

  第二個欄位會識別 CTMENU 類型的功能表資源識別碼：

- 如果指定了資源識別碼，而且第一個參數提供檔案路徑，則會從完整檔案路徑載入功能表資源。

- 如果已提供資源識別碼，但檔案路徑不是，則會從附屬 DLL 載入功能表資源。

- 如果提供完整的檔案路徑，且省略了資源識別碼，則應該載入的檔案應該是 CTO 檔。

  最後一個欄位會識別 CTMENU 資源的版本號碼。 您可以藉由變更版本號碼，再次合併功能表。

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|% CLSID_Package%|REG_SZ|`,1000,1`|用來取得功能表資訊的資源。|

 下列所有範例都位於登錄機碼 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] 下的登錄中。

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|圖形的資源識別碼值專案新專案範本。|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|新專案目錄的預設路徑。 這個目錄中的專案會顯示在 [ **新增專案嚮導** ] 對話方塊中。|
|`SortPriority`|REG_DWORD|`41 (x29)`|在 [ **新增專案** ] 對話方塊的樹狀節點中，建立專案的顯示順序。|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0表示此類型的專案只顯示在 [ **新增專案** ] 對話方塊中。|

 下列範例位於登錄機碼 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] 下的登錄中。

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|已註冊 VSPackage 的類別識別碼。|
|`UseInterface`|REG_DWORD|`1`|1表示 UI 將用來與此專案互動。 0表示沒有 UI 介面。|

 控制新專案類型的 .vsz 檔案通常包含 RELATIVE_PATH 專案。 此路徑相對於下列安裝程式索引鍵的專案類型 \ProductDir 專案中所指定的路徑：

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 例如，Enterprise Framework 專案範本會新增下列登錄專案：

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\

 這表示，如果您在 .vsz 檔案中包含 PROJECT_TYPE = EF 專案，環境會在先前指定的 ProductDir 目錄中尋找您的 .vsz 檔。

## <a name="see-also"></a>另請參閱
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)
- [使用專案 Factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

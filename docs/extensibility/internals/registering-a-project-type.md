---
title: 註冊項目類型 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05ac1f393632934f193f5f4efaaf9e5459ffbb14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705876"
---
# <a name="registering-a-project-type"></a>註冊專案類型
建立新項目類型時,必須創建註冊表項,以啟用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以識別和處理專案類型。 通常使用註冊表腳本 (.rgs) 檔案創建這些註冊表項。

 在下面的示例中,註冊表中的語句提供預設路徑和數據(如果適用),然後是包含每個語句註冊表腳本中的條目的表。 這些表提供腳本條目和有關語句的其他資訊。

> [!NOTE]
> 以下註冊表資訊旨在作為要編寫註冊項目類型的註冊表腳本中條目的類型和用途的示例。 您的實際項目及其用途可能因項目類型的特定要求而異。 您應該查看可用的範例,以尋找與您正在開發的項目類型非常相似的範例,然後查看該範例的註冊表腳本。

 以下示例來自HKEY_CLASSES_ROOT。

## <a name="example"></a>範例

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
|`@`|REG_SZ|`FigPrjFile`|具有副檔名 .figp 的項目類型檔的名稱和說明。|
|`Content Type`|REG_SZ|`Text/plain`|專案檔的內容類型。|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|用於此類型項目的預設圖示。 %MODULE% 敘述在註冊表中完成到專案類型 DLL 的預設位置。|
|`@`|REG_SZ|`&Open in Visual Studio`|將在其中打開此項目類型的預設應用程式。|
|`@`|REG_SZ|`devenv.exe "%1"`|開啟此類型的專案時將運行的預設命令。|

 以下示例來自HKEY_LOCAL_MACHINE,位於密鑰 [HKEY_LOCAL_MACHINE_軟體_Microsoft_VisualStudio_99.0Exp_包]下的註冊表中。

## <a name="example"></a>範例

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
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
|`@` (預設值)|REG_SZ|`FigPrj Project VSPackage`|此已註冊的 VSPackage(專案類型)的可本地化名稱。|
|`InprocServer32`|REG_SZ|`%MODULE%`|專案類型 DLL 的路徑。 IDE 載入此 DLL 並將 VSPackage CLSID`DllGetClassObject`<xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory>傳遞給以用於<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>建構物件。|
|`CompanyName`|REG_SZ|`Microsoft`|開發項目類型的公司的名稱。|
|`ProductName`|REG_SZ|`Figure Project Sample`|項目類型的名稱。|
|`ProductVersion`|REG_SZ|`9.0`|項目類型版本的版本號。|
|`MinEdition`|REG_SZ|`professional`|正在註冊的 VS 套件版本。|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|專案 VSPackage 的包載入鍵。 在環境啟動後載入項目時驗證金鑰。|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|包含項目類型的本地化資源的衛星 DLL 的檔名。|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|衛星 DLL 的路徑。|
|`FigProjectsEvents`|REG_SZ|有關值,請參閱語句。|確定為此自動化事件返回的文本字串。|
|`FigProjectItemsEvents`|REG_SZ|有關值,請參閱語句。|確定為此自動化事件返回的文本字串。|

 以下所有示例都位於密鑰 [HKEY_LOCAL_MACHINE_軟體_Microsoft_VisualStudio_9.0Exp_專案]下的註冊表中。

## <a name="example"></a>範例

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
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
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|此類型的項目的預設名稱。|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|要從在「包」下註冊的衛星 DLL 檢索的名稱的資源 ID。|
|`Package`|REG_SZ|`%CLSID_Package%`|在「包」下註冊的 VS 包的類 ID。|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|專案範本檔的預設路徑。 這些是新專案範本顯示的檔。|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|項目專案範本檔的預設路徑。 這些是「添加新專案」樣本顯示的檔。|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|使 IDE 能夠實現 **「打開」** 對話方塊。|
|`PossibleProjectExtensions`|REG_SZ|`figp`|IDE 用於確定要打開的專案是否由此專案類型(專案工廠)處理。 多個條目的格式是分號分隔清單。 例如「vdproj;vdp」。。|
|`DefaultProjectExtension`|REG_SZ|`.figp`|IDE 用作"儲存為"操作的預設檔名副檔名。|
|`Filter Settings`|REG_DWORD|各種,請參閱下表下的聲明和註釋。|這些設置用於設置用於在 UI 對話方塊中顯示檔的各種篩選器。|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|添加專案範本的資源 ID。|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|**"添加新項目**"範本的對話框中顯示的專案項的路徑。|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|確定「**新增新項目」** 對話框中顯示的檔案的樹節點中的排序順序。|

 下表顯示了上一個代碼段中可用的篩選器選項。

|篩選選項|描述|
|-------------------|-----------------|
|`CommonFindFilesFilter`|指示篩選器是「**在檔案中搜尋**」對話框中的常見篩選器之一。 在篩選器未標記為公共之前,常見篩選器列在篩選器清單中。|
|`CommonOpenFilesFilter`|指示篩選器是 **「打開檔」** 對話方塊中的常見篩選器之一。 在篩選器未標記為公共之前,常見篩選器列在篩選器清單中。|
|`FindInFilesFilter`|指示篩選器將是「**在檔案中搜尋**」對話框中的篩選器之一,並將列在常見篩選器之後。|
|`NotOpenFileFilter`|指示篩選器不會在 **「打開檔」** 對話方塊中使用。|
|`NotAddExistingItemFilter`|指示篩選器不會在「添加**現有項目**」對話方塊中使用。|

 預設情況下,如果篩選器沒有設置一個或多個這些標誌,則在列出公共篩選器後,「**添加現有專案**」對話框和 **「打開檔案」** 對話方塊中使用篩選器。 篩選器不在「**在檔案中尋找對話框中使用**。

 以下所有示例都位於密鑰 [HKEY_LOCAL_MACHINE_軟體_Microsoft_VisualStudio_9.0Exp_專案]下的註冊表中。

## <a name="example"></a>範例

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
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|新項目範本的資源 ID。|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|已註冊項目類型的項目的預設路徑。|
|`SortPriority`|REG_DWORD|`41 (x29)`|設置"新建專案"嚮導對話框中顯示的專案的排序順序。|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 表示此類型的專案僅在"新專案"對話框中顯示。|

 以下所有示例都位於密鑰 [HKEY_LOCAL_MACHINE_軟體_Microsoft_VisualStudio_9.0Exp_專案]下的註冊表中。

## <a name="example"></a>範例

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|None|預設值,指示以下條目用於「雜項檔」專案項目。|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|"新增新專案"樣本檔的資源 ID 值。|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|將在「**添加新項目**」對話框中顯示的項目的預設路徑。|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|建立在 **「新增新項目**」對話框的樹節點中的顯示的排序順序。|

 下面的示例位於註冊表下的關鍵 [HKEY_LOCAL_MACHINE_軟體_微軟_VisualStudio_9.0Exp_Menus]。

## <a name="example"></a>範例

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 功能表項目將 IDE 指向用於檢索功能表資訊的資源。 當此數據合併到功能表資料庫中時,註冊表的「功能表合併」部分將添加相同的密鑰。 VSPackage 不應直接修改"菜單合併"部分下的任何內容。 在下表中的「資料」欄位中,有三個逗號分隔欄位。 第一個字段識別選單資源檔的完整路徑:

- 如果省略了第一個字段,則功能表資源將從 VSPackage GUID 標識的衛星 DLL 載入。

  第二個字段識別 CTMENU 類型的選單資源 ID:

- 如果指定了資源 ID,並且檔路徑由第一個參數提供,則從完整檔路徑載入選單資源。

- 如果提供了資源 ID,但檔路徑未提供,則功能表資源將從附屬 DLL 載入。

- 如果提供了完整的文件路徑,並且省略了資源 ID,則要載入的檔應為 CTO 檔。

  最後一個字段標識 CTMENU 資源的版本號。 您可以通過更改版本號再次合併功能表。

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|%CLSID_Package%|REG_SZ|`,1000,1`|要檢索功能表資訊的資源。|

 以下所有示例都位於密鑰 [HKEY_LOCAL_MACHINE_軟體_Microsoft_VisualStudio_9.0Exp_NewProjectTemplates] 下的註冊表中。

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|圖形專案新專案範本的資源 ID 值。|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|"新項目"目錄的預設路徑。 此目錄中的項目將顯示在 **「新專案」向導**對話框中。|
|`SortPriority`|REG_DWORD|`41 (x29)`|確定專案將在 **「新專案」** 對話框的樹節點中顯示的順序。|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 表示此類型的專案僅在 **「新專案**」對話框中顯示。|

 下面的範例位於金鑰 [HKEY_LOCAL_MACHINE_軟體_Microsoft_VisualStudio_9.0Exp_已安裝產品]下的註冊表中。

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|已註冊的 VSPackage 的類 ID。|
|`UseInterface`|REG_DWORD|`1`|1 表示 UI 將用於與此專案進行互動。 0 表示沒有 UI 介面。|

 控制新項目類型的.vsz 檔案通常包含RELATIVE_PATH項。 此路徑與以下安裝程式鍵中的項目類型的 #ProductDir 項目下指定的路徑相關:

 HKEY_LOCAL_MACHINE_SOFTWARE_微軟_VisualStudio_7.0Exp_安裝程式

 例如,企業框架項目範本添加以下註冊表項:

 HKEY_LOCAL_MACHINE_SOFTWARE_微軟_VisualStudio_7.0Exp_安裝程式_產品Dir = C:程式檔_微軟視覺工作室_企業框架]

 這意味著,如果在 .vsz 檔中包含 PROJECT_TYPE_EF 條目,則環境將查找之前指定的 ProductDir 目錄中的 .vsz 檔。

## <a name="see-also"></a>另請參閱
- [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)
- [使用專案 Factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

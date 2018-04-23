---
title: 註冊專案類型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e6c91f2c92dd121cd135aef4291c7f7983206ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="registering-a-project-type"></a>註冊專案類型
當您建立新的專案類型時，您必須建立登錄項目，以便[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]辨識，並使用您的專案類型。 您通常會使用登錄指令碼 (.rgs) 檔案建立這些登錄項目。  
  
 在下列範例中，從登錄的陳述式提供預設路徑，資料情況適用時，後面接著一個資料表包含每個陳述式的登錄指令碼中的項目。 資料表提供的指令碼項目和其他資訊的陳述式。  
  
> [!NOTE]
>  下列的登錄資訊被要類型的範例，並寫入您註冊您的專案類型的登錄指令碼中的項目之用。 您的實際項目以及它們的用法可能會隨著您的專案類型的特定需求。 您應該檢閱來尋找一個非常接近您正在開發，專案類型提供的範例，然後檢閱 該範例登錄指令碼。  
  
 下列範例會從 HKEY_CLASSES_ROOT。  
  
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
|`@`|REG_SZ|`FigPrjFile`|名稱和專案類型擁有之檔案的副檔名.figp 的描述。|  
|`Content Type`|REG_SZ|`Text/plain`|專案檔的內容類型。|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|此類型的專案使用的預設圖示。 %模組 %陳述式已完成登錄 DLL 專案類型的預設位置中。|  
|`@`|REG_SZ|`&Open in Visual Studio`|將於其中開啟這個專案類型的預設應用程式。|  
|`@`|REG_SZ|`devenv.exe "%1"`|預設會在開啟此類型的專案時執行的命令。|  
  
 下列範例會從 HKEY_LOCAL_MACHINE，其位於登錄機碼 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] 下。  
  
## <a name="example"></a>範例  
  
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
|`@` （預設值）|REG_SZ|`FigPrj Project VSPackage`|可當地語系化的名稱，這個登錄 VSPackage （專案類型）。|  
|`InprocServer32`|REG_SZ|`%MODULE%`|專案類型 DLL 的路徑。 IDE 載入此 DLL，並將傳遞至 VSPackage CLSID`DllGetClassObject`取得<xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory>建構<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>物件。|  
|`CompanyName`|REG_SZ|`Microsoft`|開發專案類型的公司名稱。|  
|`ProductName`|REG_SZ|`Figure Project Sample`|專案類型的名稱。|  
|`ProductVersion`|REG_SZ|`9.0`|發行專案類型版本號碼。|  
|`MinEdition`|REG_SZ|`professional`|正在註冊 VSPackage 版本。|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|封裝載入機碼，VSPackage 專案。 啟動環境之後，載入專案時，會驗證金鑰。|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|附屬項目包含 專案類型的當地語系化的資源 DLL 的檔案名稱。|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|附屬 DLL 的路徑。|  
|`FigProjectsEvents`|REG_SZ|請參閱值的陳述式。|決定此自動化事件傳回的文字字串。|  
|`FigProjectItemsEvents`|REG_SZ|請參閱值的陳述式。|決定此自動化事件傳回的文字字串。|  
  
 下列的所有範例都位於 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 機碼下登錄。  
  
## <a name="example"></a>範例  
  
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
|`@`|REG_SZ|`FigPrj Project`|此類型的專案的預設名稱。|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|要從附屬 DLL 擷取的資源識別碼名稱的登錄的封裝底下。|  
|`Package`|REG_SZ|`%CLSID_Package%`|類別識別碼的 VSPackage 登錄的封裝底下。|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|專案範本檔案的預設路徑。 這些是新的專案範本所顯示的檔案。|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|專案項目範本檔案的預設路徑。 這些是加入新項目範本所顯示的檔案。|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|可讓實作 IDE**開啟** 對話方塊。|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|使用 IDE 來判斷是否要開啟的專案由這種專案類型 (專案 factory)。 多個項目格式是分號分隔清單。 例如 「 vdproj; vdp 」。|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|IDE 使用預設的副檔名為另存新檔作業。|  
|`Filter Settings`|REG_DWORD|各種，請參閱陳述式和註解下表。|這些設定可用來設定各種 UI 對話方塊中顯示檔案的篩選。|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|加入項目範本的資源識別碼。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|在對話方塊中顯示的專案項目路徑**加入新項目**範本。|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|決定排序順序中的樹狀結構節點中顯示的檔案**加入新項目** 對話方塊。|  
  
 下表顯示可用在先前的程式碼片段的篩選選項。  
  
|篩選選項|描述|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|表示篩選條件是其中一個常見的篩選器中**檔案中尋找** 對話方塊。 一般篩選器會列出未標記為常見的篩選條件之前篩選清單中。|  
|`CommonOpenFilesFilter`|表示篩選條件是其中一個常見的篩選器中**開啟檔案** 對話方塊。 一般篩選器會列出未標記為常見的篩選條件之前篩選清單中。|  
|`FindInFilesFilter`|指出篩選器會在篩選條件的其中一個**檔案中尋找**對話方塊方塊，然後將列在一般篩選器。|  
|`NotOpenFileFilter`|表示篩選條件不會使用在**開啟檔案** 對話方塊。|  
|`NotAddExistingItemFilter`|表示篩選條件不會使用在 [新增**現有項目**] 對話方塊。|  
  
 根據預設，如果篩選器沒有任何一個或多個旗標集，篩選用於**加入現有項目**對話方塊和**開啟檔案**之後列出常見的篩選器 對話方塊。 篩選不會用於**檔案中尋找** 對話方塊。  
  
 下列的所有範例都位於 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 機碼下登錄。  
  
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
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|新的專案範本的資源識別碼。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|預設為已註冊的專案類型的專案路徑。|  
|`SortPriority`|REG_DWORD|`41 (x29)`|集合的排序順序顯示在新專案精靈 對話方塊中的專案。|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 表示只能在 [新增專案] 對話方塊中，會顯示此類型的專案。|  
  
 下列的所有範例都位於 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 機碼下登錄。  
  
## <a name="example"></a>範例  
  
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
|`@`|REG_SZ|無|預設值，指出下列項目會針對其他檔案專案項目。|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|加入新項目範本檔案的資源識別碼值。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|預設路徑，將會顯示在項目**加入新項目** 對話方塊。|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|建立的樹狀節點中顯示的排序次序**加入新項目** 對話方塊。|  
  
 下列範例位於 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] 機碼下登錄。  
  
## <a name="example"></a>範例  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 功能表項目會指向用來擷取功能表資訊資源中的 IDE。 當此資料已合併至功能表資料庫時，相同的金鑰將會加入登錄的 MenusMerged 區段中。 VSPackage 不應該修改 MenusMerged 區段下的任何項目直接。 在下表中的資料欄位中，有三個逗號-分隔的欄位。 第一個欄位會識別功能表資源檔的完整路徑：  
  
-   如果省略第一個欄位，則從附屬 VSPackage GUID 所識別的 DLL 載入功能表資源。  
  
 第二個欄位識別類型 CTMENU 的功能表資源識別碼：  
  
-   如果指定的資源識別碼，而且第一個參數所提供的檔案路徑，從完整檔案路徑載入功能表資源。  
  
-   如果提供的資源識別碼，但不是檔案路徑，從附屬 DLL 載入功能表資源。  
  
-   如果提供的完整檔案路徑的資源識別碼省略，要載入的檔案卻 CTO 檔案。  
  
 最後一個欄位識別 CTMENU 資源的版本號碼。 您可以變更版本號碼，一次合併功能表。  
  
|名稱|類型|資料|描述|  
|----------|----------|----------|-----------------|  
|%Clsid_package%|REG_SZ|`,1000,1`|要擷取的功能表資訊的資源。|  
  
 下列的所有範例都位於 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] 機碼下登錄。  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名稱|類型|資料|描述|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|數據新專案範本的資源識別碼值。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|新的專案目錄的預設路徑。 此目錄中的項目會顯示在**新增專案 精靈** 對話方塊。|  
|`SortPriority`|REG_DWORD|`41 (x29)`|建立所在的專案將會顯示在樹狀節點的順序**新專案** 對話方塊。|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 表示此類型的專案會顯示只有**新專案** 對話方塊。|  
  
 下列範例位於 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] 機碼下登錄。  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|名稱|類型|資料|描述|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|已註冊 VSPackage 的類別 ID。|  
|`UseInterface`|REG_DWORD|`1`|1 表示 UI 將用於這個專案進行互動。 0 表示沒有 UI 介面。|  
  
 The.vsz 檔案經常控制新的專案類型包含 RELATIVE_PATH 項目。 這個路徑是相對於路徑下的下列機碼安裝程式中的專案類型 \ProductDir 項目指定：  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 例如，企業架構專案範本會加入下列登錄項目：  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 這表示如果您包含 PROJECT_TYPE = EF.vsz 檔案中，環境會發現您.vsz 檔案中指定先前的 ProductDir 目錄中的項目。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)   
 [使用 Project Factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
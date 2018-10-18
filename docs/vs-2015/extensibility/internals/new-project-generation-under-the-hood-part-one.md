---
title: 產生新專案︰ 深入來看，第一部 |Microsoft Docs
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
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 122ef6b8f1e597006fd53e6360d10d304cc760b8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302610"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>產生新專案︰深入探討，第一部分
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

有人想到要如何建立您自己的專案類型嗎？ 不知道實際發生什麼事時建立新的專案？ 讓我們來看一下在幕後，並請參閱什麼實際狀況。  
  
 有數個 Visual Studio 協調您的工作：  
  
-   它會顯示所有可用的專案類型的樹狀結構。  
  
-   它會顯示每個專案類型的應用程式範本的清單，並可讓您挑選其中一個。  
  
-   它會收集應用程式，例如專案名稱和路徑的專案資訊。  
  
-   它會將這項資訊傳遞 project factory。  
  
-   它會在目前的方案中產生專案項目和資料夾。  
  
## <a name="the-new-project-dialog-box"></a>新的 [專案] 對話方塊  
 選取新的專案的專案類型時，即開始這一切。 首先讓我們依序按一下**新的專案**上**檔案**功能表。 **新的專案** 對話方塊隨即出現，尋找如下所示：  
  
 ![[新增專案] 對話方塊](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 讓我們進一步了解。 **專案類型**樹狀目錄會列出您可以建立各種專案類型。 當您選取的專案類型，例如**Visual C# Windows**，您會看到一份應用程式範本來協助您開始使用。 **Visual Studio 安裝的範本**由 Visual Studio 安裝，而且可供您電腦的任何使用者。 可以加入新的範本，建立或收集**我的範本**和僅適用於您。  
  
 當您選取的範本，例如**Windows 應用程式**，應用程式類型的描述會出現在對話方塊中，在本例中為**具有 Windows 使用者介面建立應用程式的專案**。  
  
 在底部**新的專案** 對話方塊中，您會看到數個收集的詳細資訊的控制項。 您會看到控制項取決於專案類型，但通常包含專案**名稱**文字方塊中，**位置**文字方塊和相關**瀏覽**按鈕，然後**方案名稱**文字方塊中與相關**為方案建立目錄**核取方塊。  
  
## <a name="populating-the-new-project-dialog-box"></a>填入新的 [專案] 對話方塊  
 其中並未**新的專案** 對話方塊中取得的資訊嗎？ 在這裡正常運作，其中已被取代，有兩種機制。 **新的專案**對話方塊結合，並顯示從這兩個機制所取得的資訊。  
  
 較舊的 （已過時） 方法會使用系統登錄項目和.vsdir 檔案。 Visual Studio 開啟時，就會執行這項機制。 較新的方法會使用.vstemplate 檔案。 這項機制會在 Visual Studio 初始化時，比方說，藉由執行時執行  
  
```  
devenv /setup  
```  
  
 或  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>專案類型  
 位置和名稱**專案類型**根節點，例如**Visual C#** 並**其他語言**，取決於系統登錄項目。 組織子節點，例如**資料庫**並**智慧型裝置**，鏡像包含對應的.vstemplate 檔案的資料夾階層。 讓我們先看看的根節點。  
  
#### <a name="project-type-root-nodes"></a>專案類型的根節點  
 當[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]已初始化，它會周遊系統登錄機碼 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs 建置，並命名的根節點的子機碼**專案類型**樹狀目錄中。 這項資訊會快取以供稍後使用。 看看 TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 個索引鍵。 每個項目是 VSPackage 的 GUID。 子機碼名稱 （/ 1） 會被忽略，但它的存在表示這是**專案類型**根節點。 根節點可能又會有子機碼控制其外觀**專案類型**樹狀目錄中。 讓我們看看其中一部分。  
  
##### <a name="default"></a>(預設值)  
 這是名稱的根節點的當地語系化字串的資源識別碼。 字串資源位於附屬 DLL 選取 VSPackage 的 GUID。  
  
 在此範例中，VSPackage 的 GUID 是  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 根節點的資源識別碼 （預設值） 和 （/ 1） 是 # 2345年  
  
 如果您查詢中的鄰近的套件金鑰的 GUID，並檢查 SatelliteDll 子機碼，您可以找到包含字串資源的組件的路徑：  
  
 \<Visual Studio 安裝路徑 > \VC#\VCSPackages\1033\csprojui.dll  
  
 若要確認，請開啟 [檔案總管] csprojui.dll 拖到 Visual Studio 目錄... 字串資料表顯示資源 # 2345年標題**Visual C#**。  
  
##### <a name="sortpriority"></a>SortPriority  
 這會決定的位置中的根節點**專案類型**樹狀目錄中。  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 數目較少的優先順序，在樹狀目錄中的較高位置。  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 如果這個子機碼存在時，根節點的位置會受到開發人員設定 對話方塊。 例如，套用至物件的  
  
 DeveloperActivity REG_SZ VC #  
  
 表示 Visual C# 將根節點如果 Visual Studio 設定[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]開發。 否則，它是子節點**其他語言**。  
  
##### <a name="folder"></a>資料夾  
 如果這個子機碼存在時，根節點就會成為指定的資料夾的子節點。 可能的資料夾清單會出現在機碼  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 例如，資料庫專案項目會有符合其他專案類型中的項目 PseudoFolders 資料夾索引鍵。 因此，在**專案類型**樹狀目錄中，**資料庫專案**會是子節點的**其他專案類型**。  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>專案類型的子節點和.vstdir 檔案  
 中的子節點的位置**專案類型**樹狀結構也遵循 ProjectTemplates 資料夾中的資料夾階層。 機器的範本 (**Visual Studio 安裝的範本**)，一般位置是 files\microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ 和使用者範本 (**我的範本**)，一般位置是 documents\visual Studio 14.0\Templates\ProjectTemplates\\。 從這兩個位置的資料夾階層會合併以建立**專案類型**樹狀目錄中。  
  
 Visual Studio 中使用 C# 開發人員設定，如**專案類型**樹狀結構看起來像這樣：  
  
 ![專案類型](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 對應的 ProjectTemplates 資料夾看起來像這樣：  
  
 ![專案範本](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 當**新的專案**對話方塊隨即開啟，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]周遊 ProjectTemplates 資料夾，並重新建立其結構**專案類型**樹狀目錄中的有一些變更：  
  
-   中的根節點**專案類型**樹狀結構由應用程式範本。  
  
-   節點名稱可以當地語系化，而且可以包含特殊字元。  
  
-   可以變更排序次序。  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>尋找專案類型的根節點  
 當 Visual Studio 會周遊 ProjectTemplates 資料夾時，它會開啟所有的.zip 檔案，並擷取任何.vstemplate 檔案。 .Vstemplate 檔案使用 XML 來描述應用程式範本。 如需詳細資訊，請參閱 <<c0> [ 產生新專案： Under the Hood、 第二段](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。  
  
 \<ProjectType > 標記決定應用程式的專案類型。 比方說，\CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip 檔案包含具有此標記的 EmptyProject.vstemplate 檔案：  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType > 標記，並不在 ProjectTemplates 資料夾中，子資料夾會決定在應用程式的根節點**專案類型**樹狀目錄中。 在範例中，Windows CE 應用程式會出現下**Visual C#** 根節點，而且即使您是將 WindowsCE 資料夾移動到 VisualBasic 資料夾時，Windows CE 應用程式仍會出現在  **Visual C#** 根節點。  
  
##### <a name="localizing-the-node-name"></a>當地語系化的節點名稱  
 當 Visual Studio 會周遊 ProjectTemplates 資料夾時，它會檢查發現任何.vstdir 檔案。 .Vstdir 檔案是 XML 檔案，以控制中的專案類型的外觀**新的專案** 對話方塊。 在.vstdir 檔案中，使用\<LocalizedName > 名稱標記**專案類型**節點。  
  
 比方說，\CSharp\Database\TemplateIndex.vstdir 檔案包含此標籤：  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 這會決定名稱 [根] 節點中，在此情況下，當地語系化字串的附屬 DLL 和資源識別碼**資料庫**。 當地語系化的名稱可以包含特殊字元，並不適用於資料夾名稱，例如 **.NET**。  
  
 如果沒有\<LocalizedName > 標記存在，則專案類型的名稱是由資料夾本身**SmartPhone2003**。  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>尋找專案類型的排序次序  
 若要判斷專案類型的排序次序，請使用.vstdir 檔案\<SortOrder > 標記。  
  
 比方說，\CSharp\Windows\Windows.vstdir 檔案包含此標籤：  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 \CSharp\Database\TemplateIndex.vstdir 檔案具有的標記具有較大的值：  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 中的數字越低\<SortOrder > 標記、 樹狀目錄中的較高位置因此**Windows**節點會出現高於**資料庫**中的節點**專案類型**樹狀目錄中。  
  
 如果沒有\<SortOrder > 標記會指定專案類型，它會出現在下列包含任何專案類型的字母順序\<SortOrder > 規格。  
  
 請注意，在我的文件中有任何.vstdir 檔案 (**我的範本**) 資料夾。 使用者應用程式專案類型名稱不會當地語系化，並依字母順序顯示。  
  
#### <a name="a-quick-review"></a>快速檢閱  
 讓我們來修改**新的專案**對話方塊並建立新的使用者專案範本。  
  
1.  \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp 資料夾中新增 MyProjectNode 子資料夾。  
  
2.  MyProject.vstdir 檔案的資料夾中建立 MyProjectNode 使用任何文字編輯器。  
  
3.  您可以將這幾行加入.vstdir 檔案：  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  儲存並關閉.vstdir 檔案。  
  
5.  MyProject.vstemplate 檔案的資料夾中建立 MyProjectNode 使用任何文字編輯器。  
  
6.  這個.vstemplate 檔案中加入下列幾行：  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  儲存 the.vstemplate 檔案並關閉編輯器。  
  
8.  將新的壓縮 MyProjectNode\MyProject.zip 資料夾中的.vstemplate 檔案。  
  
9. 從 Visual Studio 命令視窗中，輸入：  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 開啟 Visual Studio。  
  
1.  開啟**新的專案** 對話方塊中，展開**Visual C#** 專案節點。  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode**做為子節點的 Visual C# 中的 [Windows] 節點下，只會出現。  
  
## <a name="see-also"></a>另請參閱  
 [產生新專案︰深入探討，第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)


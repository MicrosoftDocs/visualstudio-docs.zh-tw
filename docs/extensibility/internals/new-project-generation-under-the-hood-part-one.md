---
title: "新的專案產生： 在幕後，第一部 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 158340ad82829338bb39709573ce9e025332341a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="new-project-generation-under-the-hood-part-one"></a>新的專案產生： 在幕後，第一部
您曾經想過有關如何建立您自己的專案類型嗎？ 不知道實際發生的狀況時建立新的專案？ 讓我們看一下實際上並查看實際狀況。  
  
 有數個 Visual Studio 協調為您的工作：  
  
-   它會顯示所有可用的專案類型的樹狀結構。  
  
-   它會顯示每個專案類型的應用程式範本的清單，並可讓您選取其中一個。  
  
-   它會收集應用程式，例如專案名稱和路徑的專案資訊。  
  
-   它會將這項資訊傳遞 project factory。  
  
-   它會產生專案項目和資料夾在目前的方案。  
  
## <a name="the-new-project-dialog-box"></a>新的 [專案] 對話方塊  
 所有就會開始時選取新的專案的專案類型。 讓我們開始依序按一下**新專案**上**檔案**功能表。 **新專案** 對話方塊隨即出現，看起來像這樣：  
  
 ![新增專案對話方塊](../../extensibility/internals/media/newproject.gif "[新增專案]")  
  
 讓我們更仔細。 **專案類型**樹狀目錄會列出您可以建立各種專案類型。 當您選取的專案類型，例如**Visual C# Windows**，您會看到一份應用程式範本，讓您開始使用。 **Visual Studio 安裝的範本**由 Visual Studio 安裝，而且可供您電腦的任何使用者。 可以加入新的範本所建立，或收集**我的範本**而只會為您提供。  
  
 當您選取的範本，例如**Windows 應用程式**，應用程式類型的描述會出現在對話方塊中，則在此情況下， **Windows 使用者介面建立應用程式的專案**。  
  
 在底部**新專案**對話方塊中，您會看到數個收集的詳細資訊的控制項。 專案類型，取決於您所看到的控制項，但通常包含專案**名稱** 文字方塊中，**位置**文字方塊和相關**瀏覽**按鈕，然後**方案名稱**文字方塊和相關**為方案建立目錄**核取方塊。  
  
## <a name="populating-the-new-project-dialog-box"></a>填入新的 [專案] 對話方塊  
 其中並未**新專案**對話方塊取得的資訊嗎？ 在這裡正常運作，其中一個已被取代的方法有兩個機制。 **新專案**對話方塊結合，並顯示這兩種機制從取得的資訊。  
  
 系統登錄項目和.vsdir 檔案，則會使用舊的 （已過時） 方法。 Visual Studio 開啟時，就會執行這項機制。 較新的方法會使用.vstemplate 檔案。 這項機制會在 Visual Studio 初始化時，例如，藉由執行時執行  
  
```  
devenv /setup  
```  
  
 或  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>專案類型  
 位置和名稱**專案類型**根節點，例如**Visual C#**和**其他語言**，取決於系統登錄項目。 組織子節點，例如**資料庫**和**智慧型裝置**，鏡像處理包含對應的.vstemplate 檔案的資料夾階層。 讓我們先看看根節點。  
  
#### <a name="project-type-root-nodes"></a>專案類型的根節點  
 當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是初始化，它會周遊系統登錄機碼 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs 建置，並命名的根節點的子機碼**的型別投影**樹狀目錄中。 這項資訊會快取供稍後使用。 查看 TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 鍵。 每個項目是 VSPackage 的 GUID。 子機碼的名稱 （/ 1） 會被忽略，但其目前狀態會指出這是**專案類型**根節點。 根節點也可能有子機碼控制其外觀**專案類型**樹狀目錄中。 讓我們看看其中部分。  
  
##### <a name="default"></a>(預設值)  
 這是名稱的根節點的當地語系化字串的資源識別碼。 字串資源位於附屬 DLL 選取 VSPackage GUID。  
  
 在範例中，VSPackage GUID 是  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 根節點的資源識別碼 （預設值） 和 （/ 1） 為 # 2345年  
  
 如果查閱中的鄰近的套件金鑰的 GUID，並檢查 SatelliteDll 子機碼，您可以找到包含字串資源的組件的路徑：  
  
 \<Visual Studio 安裝路徑 > \VC#\VCSPackages\1033\csprojui.dll  
  
 若要確認這種情況，開啟 [檔案總管] 並 csprojui.dll 拖曳至 Visual Studio 目錄... 字串資料表會顯示資源 # 2345年有標題**Visual C#**。  
  
##### <a name="sortpriority"></a>SortPriority  
 這會決定的位置中的根節點**專案類型**樹狀目錄中。  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 優先順序，數目愈低愈高樹狀目錄中的位置。  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 如果這個子機碼存在，則根節點的位置由開發人員設定 對話方塊所控制。 例如，套用至物件的  
  
 DeveloperActivity REG_SZ VC #  
  
 表示 Visual C# 將根節點如果 Visual Studio 為[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]開發。 否則，它是子節點的**其他語言**。  
  
##### <a name="folder"></a>資料夾  
 如果這個子機碼存在，根節點就會成為指定之資料夾的子節點。 可能的資料夾清單隨即出現在機碼底下  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 例如，資料庫專案項目都有符合其他專案類型中的項目 PseudoFolders 資料夾金鑰。 因此，在**專案類型**樹狀目錄中，**資料庫專案**將子節點的**其他專案類型**。  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>專案類型的子節點和.vstdir 檔案  
 中的子節點位置**專案類型**樹狀結構會遵循 ProjectTemplates 資料夾中的資料夾階層。 機器範本 (**Visual Studio 安裝的範本**)，一般位置是 files\microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\，並提供使用者範本 (**我的範本**)，一般位置是 documents\visual Studio 14.0\Templates\ProjectTemplates\\。 從這兩個位置的資料夾階層會合併，以建立**專案類型**樹狀目錄中。  
  
 Visual Studio 中以 C# 開發人員設定，如**專案類型**樹狀目錄中看起來像這樣：  
  
 ![專案類型](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 對應 ProjectTemplates 資料夾看起來像這樣：  
  
 ![專案範本](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 當**新專案**對話方塊隨即開啟，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]周遊 ProjectTemplates 資料夾，並重新建立它的結構中**專案類型**樹狀目錄中的某些變更：  
  
-   中的根節點**專案類型**樹狀結構由應用程式範本。  
  
-   節點名稱可以當地語系化，而且可以包含特殊字元。  
  
-   可以變更排序次序。  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>尋找專案類型的根節點  
 當 Visual Studio 會周遊 ProjectTemplates 資料夾時，它會開啟所有的.zip 檔案，並擷取任何.vstemplate 檔案。 這個.vstemplate 檔案會使用 XML 來描述應用程式範本。 如需詳細資訊，請參閱[產生新的專案： 在其實、 第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。  
  
 \<ProjectType > 標記決定應用程式的專案類型。 例如，\CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip 檔案包含具有此標記的 EmptyProject.vstemplate 檔案：  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType > 標記和不在 ProjectTemplates 資料夾中，子資料夾可決定在應用程式的根節點**專案類型**樹狀目錄中。 在範例中，Windows CE 應用程式會出現底下**Visual C#**根節點，而且即使您是將 WindowsCE 資料夾移至 VisualBasic 資料夾，則 Windows CE 應用程式仍會出現在  **Visual C#**根節點。  
  
##### <a name="localizing-the-node-name"></a>當地語系化的節點名稱  
 當 Visual Studio 會周遊 ProjectTemplates 資料夾時，它會檢查它找到任何.vstdir 檔案。 .Vstdir 檔案是控制項的外觀中的專案類型的 XML 檔案**新專案** 對話方塊。 在.vstdir 檔案中，使用\<LocalizedName > 標記名稱**專案類型**節點。  
  
 例如，\CSharp\Database\TemplateIndex.vstdir 檔案會包含此標記：  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 這會決定名稱的根節點，在此案例中的當地語系化字串的附屬 DLL 和資源識別碼**資料庫**。 當地語系化的名稱可以包含特殊字元，並不適用於資料夾名稱，例如**.NET**。  
  
 如果沒有\<LocalizedName > 標記存在，則該專案類型的命名方式是資料夾本身， **SmartPhone2003**。  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>尋找專案類型的排序次序  
 若要判斷專案類型的排序次序，請使用.vstdir 檔案\<SortOrder > 標記。  
  
 例如，\CSharp\Windows\Windows.vstdir 檔案會包含此標記：  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 \CSharp\Database\TemplateIndex.vstdir 檔案具有的標記具有較大的值：  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 中的位置愈低的數字\<SortOrder > 標記，愈高的位置在樹狀目錄中，所以**Windows**節點會出現高於**資料庫**中的節點**專案類型**樹狀目錄中。  
  
 如果沒有\<SortOrder > 標記指定的專案類型，它會出現在下列任何包含的專案類型的字母順序\<SortOrder > 規格。  
  
 請注意，在 我的文件中有任何.vstdir 檔案 (**我的範本**) 資料夾。 未當地語系化使用者應用程式專案型別名稱，並依字母順序顯示。  
  
#### <a name="a-quick-review"></a>快速檢閱  
 讓我們來修改**新專案**對話方塊並建立新的使用者專案範本。  
  
1.  加入 \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp 資料夾 MyProjectNode 子資料夾。  
  
2.  MyProject.vstdir 檔案的資料夾中建立 MyProjectNode 使用任何文字編輯器。  
  
3.  將下列行加入.vstdir 檔案：  
  
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
  
8.  .Vstemplate 檔案傳送到新的壓縮 MyProjectNode\MyProject.zip 資料夾。  
  
9. 從 Visual Studio 命令視窗中，輸入：  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 開啟 Visual Studio。  
  
1.  開啟**新專案**對話方塊方塊中，展開  **Visual C#**專案節點。  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode**會顯示為子節點的 Visual C# 中的 Windows 節點的下方。  
  
## <a name="see-also"></a>請參閱  
 [產生新專案︰深入探討，第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
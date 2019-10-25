---
title: 新專案產生：幕後，第一部 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41b2b229fe343c9f6d515ba757e4bd976ee7fda5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726520"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>產生新專案︰深入探討，第一部分
您是否想要瞭解如何建立您自己的專案類型？ 想知道當您建立新專案時，實際發生什麼事？ 讓我們看看幕後的內容，並查看真正的狀況。

 有數個工作會為您 Visual Studio 座標：

- 它會顯示所有可用專案類型的樹狀結構。

- 它會顯示每個專案類型的應用程式範本清單，並讓您挑選一個。

- 它會收集應用程式的專案資訊，例如專案名稱和路徑。

- 它會將此資訊傳遞至專案 factory。

- 它會在目前的方案中產生專案專案和資料夾。

## <a name="the-new-project-dialog-box"></a>[新增專案] 對話方塊
 當您選取新專案的專案類型時，就會開始。 首先，**按一下 [檔案**] 功能表上的 [**新增專案**]。 [**新增專案**] 對話方塊隨即出現，並看起來像這樣：

 ![[新增專案] 對話方塊](../../extensibility/internals/media/newproject.gif "NewProject")

 讓我們進一步瞭解。 [**專案類型**] 樹狀目錄會列出您可以建立的各種專案類型。 當您選取專案類型（例如**Visual C# Windows**）時，您會看到可讓您開始使用的應用程式範本清單。 **Visual Studio 安裝的範本**會由 Visual Studio 安裝，並可供電腦的任何使用者使用。 您建立或收集的新範本可以新增至 [**我的範本**]，而且只能供您使用。

 當您選取如**Windows 應用程式**的範本時，應用程式類型的描述會出現在對話方塊中;在此情況下，**是用來建立具有 Windows 使用者介面之應用程式的專案**。

 在 [**新增專案**] 對話方塊的底部，您會看到數個可收集詳細資訊的控制項。 您看到的控制項視專案類型而定，但通常包括 [專案**名稱**] 文字方塊、[**位置**] 文字方塊和相關的 **[流覽]** 按鈕，以及方案的 [**方案名稱**] 文字方塊和相關的 [**建立目錄]。** 核取方塊。

## <a name="populating-the-new-project-dialog-box"></a>填入 [新增專案] 對話方塊
 [**新增專案**] 對話方塊從何處取得其資訊？ 這裡有兩種機制可供使用，其中一個已被取代。 [**新增專案**] 對話方塊結合並顯示從這兩種機制取得的資訊。

 較舊的（已淘汰）方法會使用系統登錄機碼目和 vsdir 檔案。 此機制會在 Visual Studio 開啟時執行。 較新的方法會使用 .vstemplate 檔案。 這項機制會在 Visual Studio 初始化（例如，藉由執行

```
devenv /setup
```

 或

```
devenv /installvstemplates
```

### <a name="project-types"></a>專案類型
 **專案類型**根節點的位置和名稱，例如 **C#視覺**和**其他語言**，是由系統登錄機碼目所決定。 子節點的組織（例如**資料庫**和**智慧型裝置**）會鏡像包含對應 .vstemplate 檔案之資料夾的階層。 讓我們先看一下根節點。

#### <a name="project-type-root-nodes"></a>專案類型根節點
 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 初始化時，它會遍歷系統登錄鍵 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs 的子機碼，以建立並命名**專案類型**樹狀結構的根節點。 此資訊會進行快取以供稍後使用。 查看 TemplateDirs \\ {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\/1 鍵。 每個專案都是 VSPackage GUID。 已忽略子機碼（/1）的名稱，但其存在表示這是**專案類型**根節點。 根節點可能會在 [**專案類型**] 樹狀結構中，有數個子機控制其外觀。 讓我們來看看其中的一些專案。

##### <a name="default"></a>(預設值)
 這是命名根節點之當地語系化字串的資源識別碼。 字串資源位於 VSPackage GUID 所選取的附屬 DLL 中。

 在此範例中，VSPackage GUID 為

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 根節點的資源識別碼（預設值）（/1）是 #2345

 如果您在 [鄰近的套件] 索引鍵中查閱 GUID，並檢查 SatelliteDll 子機碼，您可以找到包含字串資源之元件的路徑：

 \<Visual Studio 安裝路徑 > \VC#\VCSPackages\1033\csprojui.dll

 若要確認這一點，請開啟 [檔案瀏覽器]，然後將 [csprojui] 拖曳至 Visual Studio 目錄。 字串表顯示資源 #2345 的標題為 [**視覺效果C#** ]。

##### <a name="sortpriority"></a>SortPriority
 這會決定根節點在 [**專案類型**] 樹狀結構中的位置。

 SortPriority REG_DWORD 0x00000014 （20）

 優先順序愈低，樹狀結構中的位置愈高。

##### <a name="developeractivity"></a>DeveloperActivity
 如果這個子機碼存在，則根節點的位置是由 [開發人員設定] 對話方塊所控制。 例如，套用至物件的

 DeveloperActivity REG_SZVC#

 表示如果已C#針對 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 開發設定 Visual Studio，則視覺效果將會是根節點。 否則，它會是**其他語言**的子節點。

##### <a name="folder"></a>資料夾
 如果這個子機碼存在，則根節點會變成指定資料夾的子節點。 可能的資料夾清單會出現在 [機碼] 底下

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 例如，[資料庫專案] 專案的資料夾索引鍵會符合 PseudoFolders 中的其他專案類型專案。 因此，在 [**專案類型**] 樹狀目錄中，**資料庫專案**將是**其他專案類型**的子節點。

#### <a name="project-type-child-nodes-and-vstdir-files"></a>專案類型子節點和 vstdir 檔
 [**專案類型**] 樹狀結構中的子節點位置會遵循 ProjectTemplates 資料夾中的資料夾階層。 針對電腦範本（**Visual Studio 安裝的範本**），一般位置是 \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\，而對於使用者範本（**我的範本**）而言，一般的位置是 \My Documents \Visual Studio 14.0 \ Templates\ProjectTemplates \\。 這兩個位置的資料夾階層會合並，以建立**專案類型**樹狀結構。

 若為具有C#開發人員設定的 Visual Studio，[**專案類型**] 樹狀結構看起來會像這樣：

 ![專案類型](../../extensibility/internals/media/projecttypes.png "ProjectTypes")

 對應的 ProjectTemplates 資料夾看起來像這樣：

 ![專案範本](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")

 當 [**新增專案**] 對話方塊開啟時，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會遍歷 ProjectTemplates 資料夾，並在 [**專案類型**] 樹狀目錄中重新建立其結構，但有一些變更：

- [**專案類型**] 樹狀結構中的根節點是由應用程式範本決定。

- 節點名稱可以當地語系化，而且可以包含特殊字元。

- 您可以變更排序次序。

##### <a name="finding-the-root-node-for-a-project-type"></a>尋找專案類型的根節點
 當 Visual Studio 遍歷 ProjectTemplates 資料夾時，它會開啟所有 .zip 檔案，並解壓縮任何 .vstemplate 檔案。 .Vstemplate 檔案使用 XML 來描述應用程式範本。 如需詳細資訊，請參閱[新的專案產生：在幕後，第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。

 @No__t_0ProjectType > 標記會決定應用程式的專案類型。 例如，\CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip 檔案包含具有此標記的 EmptyProject：

```
<ProjectType>CSharp</ProjectType>
```

 @No__t_0ProjectType > 標記，而不是 ProjectTemplates 資料夾中的子資料夾，會決定應用程式在 [**專案類型**] 樹狀結構中的根節點。 在此範例中，Windows CE 應用程式會出現**在C#視覺**根節點下，即使您要將 WindowsCE 資料夾移至 [...] 資料夾，Windows CE 應用程式仍會出現在**視覺C#效果**根目錄底下節點.

##### <a name="localizing-the-node-name"></a>當地語系化節點名稱
 當 Visual Studio 流經 ProjectTemplates 資料夾時，它會檢查它找到的任何 vstdir 檔案。 Vstdir 檔案是一個 XML 檔案，可控制 [**新增專案**] 對話方塊中專案類型的外觀。 在 vstdir 檔案中，使用 \<LocalizedName > 標記來命名 [**專案類型**] 節點。

 例如，\CSharp\Database\TemplateIndex.vstdir 檔案包含此標記：

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 這會決定用來命名根節點（在此案例中為**資料庫**）之當地語系化字串的附屬 DLL 和資源識別碼。 當地語系化的名稱可以包含資料夾名稱無法使用的特殊字元，例如 **.net**。

 如果沒有 \<LocalizedName > 標記，則專案類型是由資料夾本身命名， **SmartPhone2003**。

##### <a name="finding-the-sort-order-for-a-project-type"></a>尋找專案類型的排序次序
 若要判斷專案類型的排序次序，vstdir 檔案會使用 \<SortOrder > 標記。

 例如，\CSharp\Windows\Windows.vstdir 檔案包含此標記：

```
<SortOrder>5</SortOrder>
```

 \CSharp\Database\TemplateIndex.vstdir 檔案具有較大值的標記：

```
<SortOrder>5000</SortOrder>
```

 @No__t_0SortOrder > 標記中的數位越低，樹狀結構中的位置就愈高，因此**Windows**節點會顯示在 [**專案類型**] 樹狀結構的 [**資料庫**] 節點上方。

 如果未指定專案類型的 \<SortOrder > 標記，則會依照包含 \<SortOrder > 規格的任何專案類型，按照字母順序顯示。

 請注意，[我的文件] （**我的範本**）資料夾中沒有 vstdir 檔案。 使用者應用程式專案類型名稱不會當地語系化，而且會依字母順序顯示。

#### <a name="a-quick-review"></a>快速審核
 讓我們修改 [**新增專案**] 對話方塊，並建立新的使用者專案範本。

1. 將 MyProjectNode 子資料夾新增至 \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\CSharp 資料夾。

2. 使用任何文字編輯器，在 MyProjectNode 資料夾中建立 MyProject vstdir 檔案。

3. 將下列幾行新增至 vstdir 檔案：

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. 儲存並關閉 vstdir 檔案。

5. 使用任何文字編輯器，在 MyProjectNode 資料夾中建立 MyProject。

6. 將下列幾行新增至 .vstemplate 檔案：

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. 儲存 .vstemplate 檔案，然後關閉編輯器。

8. 將 .vstemplate 檔案傳送到新的壓縮 MyProjectNode\MyProject.ZIP 檔案夾。

9. 從 [Visual Studio 命令] 視窗中，輸入：

    ```
    devenv /installvstemplates
    ```

   開啟 Visual Studio。

10. 開啟 [**新增專案**] 對話方塊，然後展開 **[ C#視覺效果**專案] 節點。

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    在 Windows 節點底下， **MyProjectNode**會顯示C#為 [視覺效果] 的子節點。

## <a name="see-also"></a>請參閱
- [產生新專案︰深入探討，第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
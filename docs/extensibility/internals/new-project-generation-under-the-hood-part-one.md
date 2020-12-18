---
title: 新專案產生：在幕後，第一個部分 |Microsoft Docs
description: 您可以在建立自己的專案類型 (第1部（共 2) ）中，深入瞭解 Visual Studio 整合式開發環境 (IDE) 的狀況。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec16895e71788f160e0ce6025f35b4dff02d7d2f
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668881"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>新專案產生：一探究竟，第一部份
您是否想要瞭解如何建立自己的專案類型？ 想知道當您建立新專案時實際發生什麼事？ 讓我們看看幕後的內容，並看看真正的進展。

 有幾項工作會為您 Visual Studio 座標：

- 它會顯示所有可用專案類型的樹狀結構。

- 它會顯示每個專案類型的應用程式範本清單，並讓您挑選一個。

- 它會收集應用程式的專案資訊，例如專案名稱和路徑。

- 它會將此資訊傳遞至專案 factory。

- 它會在目前的方案中產生專案專案和資料夾。

## <a name="the-new-project-dialog-box"></a>[新增專案] 對話方塊
 當您選取新專案的專案類型時，就會開始。 讓我們從按一下 [檔案] 功能表上 **的 [** **新增專案**] 開始。 [ **新增專案** ] 對話方塊隨即出現，並看起來像這樣：

 ![[新增專案] 對話方塊的螢幕擷取畫面。](../../extensibility/internals/media/newproject.gif)

 讓我們進一步了解。 [ **專案類型** ] 樹狀目錄會列出您可以建立的各種專案類型。 當您選取專案類型（如 **Visual c # Windows**）時，您會看到可讓您開始使用的應用程式範本清單。 **Visual Studio 安裝的範本** 是由 Visual Studio 安裝，且可供電腦的任何使用者使用。 您建立或收集的新範本可以新增至 **我的範本** ，而且只能供您使用。

 當您選取範本（例如 **Windows 應用程式**）時，此應用程式類型的描述會出現在對話方塊中;在此情況下，會 **使用 Windows 使用者介面來建立應用程式的專案**。

 在 [ **新增專案** ] 對話方塊的底部，您會看到數個可收集詳細資訊的控制項。 您看到的控制項取決於專案類型，但通常會包含 [專案 **名稱** ] 文字方塊、[ **位置** ] 文字方塊和 [相關 **流覽]** 按鈕，以及 [方案 **名稱** ] 文字方塊和 [ **方案的相關建立目錄** ] 核取方塊。

## <a name="populating-the-new-project-dialog-box"></a>填入 [新增專案] 對話方塊
 [ **新增專案** ] 對話方塊從哪裡取得其資訊？ 這裡有兩種機制，其中一個已被取代。 [ **新增專案** ] 對話方塊結合並顯示從這兩種機制取得的資訊。

 舊版 (淘汰的) 方法會使用系統登錄機碼目和 vsdir 檔案。 當 Visual Studio 開啟時，就會執行此機制。 較新的方法會使用 .vstemplate 檔案。 這項機制會在 Visual Studio 初始化時執行，例如，藉由執行

```
devenv /setup
```

 或

```
devenv /installvstemplates
```

### <a name="project-types"></a>專案類型
 **專案類型** 的位置和名稱（例如 **Visual c #** 和 **其他語言**）是由系統登錄機碼目所決定。 子節點（例如 **資料庫** 和 **智慧型裝置**）的組織會鏡像包含對應之 .vstemplate 檔案的資料夾階層。 讓我們先看看根節點。

#### <a name="project-type-root-nodes"></a>專案類型根節點
 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 初始化時，它會遍歷系統登錄機碼 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs 的子機碼，以建立並命名 **專案類型** 樹狀結構的根節點。 這項資訊會快取以供稍後使用。 查看 TemplateDirs \\ {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 鍵。 每個專案都是 VSPackage 的 GUID。 子機碼 (/1) 的名稱會被忽略，但其存在表示這是 **專案類型** 的根節點。 根節點可能會有數個子機碼可控制其在 **專案類型** 樹狀結構中的外觀。 讓我們來看看其中的部分。

##### <a name="default"></a>(預設值)
 這是命名根節點之當地語系化字串的資源識別碼。 字串資源位於 VSPackage GUID 所選取的附屬 DLL 中。

 在此範例中，VSPackage GUID 為

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 而根節點的資源識別碼 (預設值)  (/1) 是 #2345

 如果您查閱附近套件索引鍵中的 GUID，並檢查 SatelliteDll 子機碼，您可以找到包含字串資源的元件路徑：

 \<Visual Studio installation path>\VC # \VCSPackages\1033\csprojui.dll

 若要確認這一點，請開啟檔案總管，並將 csprojui.dll 拖曳至 Visual Studio 目錄。 字串表格顯示資源 #2345 具有 **Visual c #** 的標題。

##### <a name="sortpriority"></a>SortPriority
 這會決定根節點在 **專案類型** 樹狀結構中的位置。

 SortPriority REG_DWORD 0x00000014 (20) 

 優先權的數目愈低，樹狀結構中的位置愈高。

##### <a name="developeractivity"></a>DeveloperActivity
 如果有這個子機碼，則根節點的位置是由 [開發人員設定] 對話方塊所控制。 例如，

 DeveloperActivity REG_SZ VC#

 指出如果已針對開發設定 Visual Studio，則 Visual c # 會是根節點 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 。 否則，它會是 **其他語言** 的子節點。

##### <a name="folder"></a>資料夾
 如果有這個子機碼，根節點就會變成指定之資料夾的子節點。 可能的資料夾清單會出現在機碼底下

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 例如，資料庫專案專案的資料夾索引鍵符合 PseudoFolders 中的其他專案類型專案。 因此，在 **專案類型** 樹狀結構中， **資料庫專案** 將會是 **其他專案類型** 的子節點。

#### <a name="project-type-child-nodes-and-vstdir-files"></a>專案類型的子節點和 vstdir 檔案
 **專案類型** 樹狀結構中的子節點位置會遵循 >\templates\projecttemplates\csharp\helloworld\ 資料夾中的資料夾階層。 針對 (**Visual Studio 安裝的範本**) 的電腦範本，一般位置是 \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\，而針對 (**範本**) 的使用者範本，一般位置是 \My Documents\Visual Studio 14.0 \ Templates\ProjectTemplates \\ 。 這兩個位置的資料夾階層會合並以建立 **專案類型** 樹狀結構。

 針對使用 c # 開發人員設定的 Visual Studio， **專案類型** 樹狀結構看起來像這樣：

 ![使用 c # 開發人員設定 Visual Studio 中的專案類型資料夾樹狀結構的螢幕擷取畫面。](../../extensibility/internals/media/projecttypes.png)

 對應的 >\templates\projecttemplates\csharp\helloworld\ 資料夾看起來像這樣：

 ![使用 c # 開發人員設定 Visual Studio 中 [專案範本] 資料夾樹狀結構的螢幕擷取畫面。](../../extensibility/internals/media/projecttemplates.png)

 當 [ **新增專案** ] 對話方塊開啟時，會 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在 >\templates\projecttemplates\csharp\helloworld\ 資料夾中進行，並在 **專案類型** 樹狀結構中重新建立其結構，但有一些變更：

- **專案類型** 樹狀結構中的根節點是由應用程式範本所決定。

- 節點名稱可以當地語系化，而且可以包含特殊字元。

- 排序次序可以變更。

##### <a name="finding-the-root-node-for-a-project-type"></a>尋找專案類型的根節點
 當 Visual Studio 流經 >\templates\projecttemplates\csharp\helloworld\ 資料夾時，它會開啟所有 .zip 檔案並解壓縮任何 .vstemplate 檔案。 .Vstemplate 檔案會使用 XML 來描述應用程式範本。 如需詳細資訊，請參閱 [新專案產生：幕後的第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。

 \<ProjectType>標記會決定應用程式的專案類型。 例如，\CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip 檔案包含具有此標記的 EmptyProject .vstemplate 檔案：

```
<ProjectType>CSharp</ProjectType>
```

 \<ProjectType>標記（而不是 >\templates\projecttemplates\csharp\helloworld\ 資料夾中的子資料夾）會決定應用程式在 [**專案類型**] 樹狀結構中的根節點。 在此範例中，Windows CE 的應用程式會出現在 **Visual c #** 根節點之下，即使您要將 WindowsCE 資料夾移至 [[]] 資料夾，Windows CE 應用程式仍會顯示在 **visual c #** 根節點下。

##### <a name="localizing-the-node-name"></a>將節點名稱當地語系化
 當 Visual Studio 流經 >\templates\projecttemplates\csharp\helloworld\ 資料夾時，它會檢查找到的任何 vstdir 檔案。 Vstdir 檔案是一個 XML 檔案，可在 [ **新增專案** ] 對話方塊中控制專案類型的外觀。 在 vstdir 檔案中，使用 \<LocalizedName> 標記為 **專案類型** 節點命名。

 例如，\CSharp\Database\TemplateIndex.vstdir 檔案包含此標記：

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 這會決定命名根節點之當地語系化字串的附屬 DLL 和資源識別碼（在此案例中為 **資料庫**）。 當地語系化名稱可以包含不適用資料夾名稱的特殊字元，例如 **.net**。

 如果沒有 \<LocalizedName> 標記，則專案類型是由資料夾本身（ **SmartPhone2003**）命名。

##### <a name="finding-the-sort-order-for-a-project-type"></a>尋找專案類型的排序次序
 若要判斷專案類型的排序次序，vstdir 檔案會使用 \<SortOrder> 標記。

 例如，\CSharp\Windows\Windows.vstdir 檔案包含此標記：

```
<SortOrder>5</SortOrder>
```

 \CSharp\Database\TemplateIndex.vstdir 檔案的標記具有較大的值：

```
<SortOrder>5000</SortOrder>
```

 標記中的數位愈低 \<SortOrder> ，樹狀結構中的位置愈大，因此 **Windows** 節點出現在 [**專案類型**] 樹狀結構中的 [**資料庫**] 節點上方。

 如果未 \<SortOrder> 指定任何專案類型的標記，則會依包含規格的任何專案類型，依字母順序顯示 \<SortOrder> 。

 請注意，[ **我的範本** ] (我的檔中沒有任何 vstdir 檔案) 資料夾。 使用者應用程式專案類型名稱不會當地語系化，而且會依字母順序顯示。

#### <a name="a-quick-review"></a>快速審核
 讓我們修改 [ **新增專案** ] 對話方塊，並建立新的使用者專案範本。

1. 將 MyProjectNode 子資料夾新增至 \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\CSharp 資料夾。

2. 使用任何文字編輯器，在 MyProjectNode 資料夾中建立 MyProject. vstdir 檔案。

3. 將下列幾行新增至 vstdir 檔案：

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. 儲存並關閉 vstdir 檔案。

5. 使用任何文字編輯器，在 MyProjectNode 資料夾中建立 MyProject .vstemplate 檔案。

6. 將下列幾行新增至 .vstemplate 檔案：

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. 儲存 .vstemplate 檔案，然後關閉編輯器。

8. 將 .vstemplate 檔案傳送到新的壓縮 MyProjectNode\MyProject.zip 資料夾。

9. 從 Visual Studio 命令視窗中，輸入：

    ```
    devenv /installvstemplates
    ```

   開啟 Visual Studio。

10. 開啟 [ **新增專案** ] 對話方塊，然後展開 **Visual c #** 專案節點。

    ![[新增專案] 對話方塊中的 [專案類型] 資料夾樹狀結構的螢幕擷取畫面，其中已展開 Visual c # 專案節點下的 MyProjectNode。](../../extensibility/internals/media/myprojectnode.png)

    **MyProjectNode** 會顯示為 Visual c # 的子節點，就在 Windows 節點下。

## <a name="see-also"></a>另請參閱
- [新專案產生：一探究竟，第二部份](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

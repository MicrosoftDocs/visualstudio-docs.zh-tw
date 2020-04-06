---
title: 新專案生成:在引擎蓋下,第一部分 |微軟文件
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
ms.openlocfilehash: aca35e85e57a07a2b411a23d81b99cff9983b9c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707060"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>產生新專案︰深入探討，第一部分
曾經考慮過如何創建自己的項目類型? 想知道創建新專案時實際會發生什麼情況? 讓我們看看引擎蓋下,看看到底發生了什麼。

 Visual Studio 為您協調了幾個任務:

- 它顯示所有可用項目類型的樹。

- 它顯示每個項目類型的應用程式樣本清單,並允許您選擇一個範本。

- 它收集應用程式的專案資訊,如專案名稱和路徑。

- 它將此信息傳遞給項目工廠。

- 它在當前解決方案中生成專案項和資料夾。

## <a name="the-new-project-dialog-box"></a>新項目對話框
 當您為新項目選擇項目類型時,一切就開始了。 讓我們首先按下 **「檔**」功能表上的 **「新專案**」。 此時將顯示 **「新項目**」對話框,如下所示:

 ![[New Project] \(新增專案\) 對話方塊](../../extensibility/internals/media/newproject.gif "NewProject")

 讓我們進一步了解。 「**項目類型」** 樹列出了您可以建立的各種項目類型。 當您選擇項目類型(如**Visual C# Windows)** 時,您將看到一個應用程式樣本清單來説明您入門。 **Visual Studio 安裝的範本**由 Visual Studio 安裝,可供電腦的任何使用者使用。 您創建或收集的新範本可以添加到 **「我的範本」中**,並且僅對您可用。

 當您選擇像 Windows**應用程式**這樣的範本時,應用程式類型的說明將顯示在對話方塊中;但是,在對話方塊中,將顯示應用程式類型的說明。在這種情況下,**用於使用 Windows 使用者介面建立應用程式的專案**。

 在 **「新項目」** 對話框的底部,您將看到幾個收集詳細資訊的控制項。 您看到的控制項取決於項目類型,但通常包括專案**名稱**文字框、**位置**文字框和相關 **「瀏覽」** 按鈕,以及**解決方案名稱**文本框和**解決方案的相關"創建目錄**"複選框。

## <a name="populating-the-new-project-dialog-box"></a>填充新項目對話框
 **新項目**對話框從何處獲取其資訊? 這裡有兩種機制在起作用,其中一種是棄用的。 "**新項目**"對話框合併並顯示從這兩個機制獲得的資訊。

 較舊的(已棄用)方法使用系統註冊表項和 .vsdir 檔。 此機制在可視化工作室打開時運行。 較新的方法使用 .vstemplate 檔。 此機制在可視化工作室初始化時運行,例如,通過運行

```
devenv /setup
```

 或

```
devenv /installvstemplates
```

### <a name="project-types"></a>專案類型
 **Project 類型**根節點(如**Visual C#** **和其他語言**)的位置和名稱由系統註冊表項確定。 子節點(如**資料庫**和**智慧設備**)的組織鏡像包含相應 .vstemplate 檔案的資料夾的層次結構。 讓我們先看一下根節點。

#### <a name="project-type-root-nodes"></a>專案類型根節點
 初始[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]化時,它將遍歷系統註冊表項HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio_14.0_NewProjectTemplates_TemplateDirs的子鍵,以生成和命名**項目類型**樹的根節點。 此資訊將緩存供以後使用。 查看範本 Dirs\\[FAE04EC1-301F-11D3-BF4B-00C04F79EFBC]\\/1 鍵。 每個條目都是 VSPackage GUID。 子鍵 (/1) 的名稱將被忽略,但其存在表明這是**項目類型**根節點。 根節點可能又具有多個子鍵,這些子鍵控制其在**Project 類型**樹中的外觀。 讓我們來看看其中的一些。

##### <a name="default"></a>(預設值)
 這是命名根節點的當地語系化字串的資源 ID。 字串資源位於 VSPackage GUID 選擇的衛星 DLL 中。

 這個範例中,VS 套件 GUID 是

 [FAE04EC1-301F-11D3-BF4B-00C04F79EFBC]

 根節點 (/1) 的資源 ID(預設值)#2345

 如果在附近的「包」鍵中尋找 GUID 並檢查 SatelliteDll 子鍵,則可以找到包含字串資源的程式集的路徑:

 \<視覺工作室安裝路徑>_VC_VCS 包\1033\csprojui.dll

 要驗證這一點,請打開檔案資源管理器並將 csprojui.dll 拖動到可視化工作室目錄中。 字串表顯示資源#2345具有 Visual **C#** 的標題。

##### <a name="sortpriority"></a>排序優先權
 這將確定根節點在**項目類型**樹中的位置。

 排序優先權REG_DWORD 0x00000014 (20)

 優先順序的數量越低,樹中的位置越高。

##### <a name="developeractivity"></a>開發人員活動
 如果存在此子鍵,則根節點的位置由"開發人員設置"對話框控制。 例如，

 開發人員活動REG_SZ VC#

 指示如果為[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]開發設置了 Visual Studio,則 Visual C++ 將成為根節點。 否則,它將是**其他語言**的子節點。

##### <a name="folder"></a>資料夾
 如果存在此子鍵,則根節點將成為指定資料夾的子節點。 這個鍵下會顯示可能的資料夾清單

 HKEY_LOCAL_MACHINE_SOFTWARE_微軟_VisualStudio_11.0\新專案範本\偽資料夾

 例如,資料庫專案條目具有與偽資料夾中的「其他項目類型」條目匹配的資料夾鍵。 因此,在**專案類型**樹中,**資料庫專案**將是**其他專案類型的**子節點。

#### <a name="project-type-child-nodes-and-vstdir-files"></a>專案類型子節點和 .vstdir 檔案
 **"專案類型'** 樹中的子節點的位置遵循 ProjectTemplates 資料夾中資料夾的層次結構。 對於機器範本 **(Visual Studio 安裝的範本**),典型位置是 [程式檔]微軟可視化工作室 14.0\Common7_IDE_ProjectTemplates]和使用者範本(**我的範本**),典型位置是 [我的文檔]Visual Studio\\14.0_範本\專案範本 。 合併這兩個位置的資料夾層次結構以創建**專案類型**樹。

 對於具有 C# 開發人員設定的視覺化工作室,**專案類型**樹如下所示:

 ![專案類型](../../extensibility/internals/media/projecttypes.png "專案類型")

 相應的 ProjectTemplates 資料夾如下所示:

 ![專案範本](../../extensibility/internals/media/projecttemplates.png "專案範本")

 開啟**新項目**對話框時,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]您要建立 ProjectTemplates 資料夾,並在 **「項目類型**」 樹中重新建立其結構,並進行一些變更:

- **項目類型**樹中的根節點由應用程式範本確定。

- 節點名稱可以當地語系化,可以包含特殊字元。

- 可以更改排序順序。

##### <a name="finding-the-root-node-for-a-project-type"></a>尋找項目類型的根節點
 當 Visual Studio 遍歷 ProjectTemplates 資料夾時,它會打開所有 .zip 檔案並提取任何 .vstemplate 檔。 .vstemplate 檔案使用 XML 來描述應用程式範本。 有關詳細資訊,請參閱[新專案生成:在罩下,第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。

 項目\<類型>標記確定應用程式的項目類型。 例如,[CSharp]智慧設備\WindowsCE_1033_WindowsCE-emptyProject.zip 檔包含一個 EmptyProject.vstemplate 檔,該檔具有以下標記:

```
<ProjectType>CSharp</ProjectType>
```

 ProjectType>\<標籤(而不是 ProjectTemplates 資料夾中的子資料夾)確定 **「項目類型**」樹中的應用程式的根節點。 在此範例中,Windows CE 應用程式將顯示在 Visual **C++** 根節點下,即使您要將 WindowsCE 資料夾移動到 VisualBasic 資料夾,Windows CE 應用程式仍將顯示在**Visual C++** 根節點下。

##### <a name="localizing-the-node-name"></a>本地化節點名稱
 當 Visual Studio 遍歷 ProjectTemplates 資料夾時,它會檢查它找到的任何 .vstdir 檔。 .vstdir 檔案是一個 XML 檔,用於控制項目類型在 **"新專案"** 對話框中的外觀。 在 .vstdir 檔案中\<,使用 當地語系化名稱>標記來命名**專案類型**節點。

 例如,[CSharp]資料庫_樣本索引.vstdir 檔包含此標記:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 這會確定命名根節點的本地化字串的附屬 DLL 和資源 ID,在這種情況下,**為資料庫**。 本地化名稱可以包含不適用於資料夾名稱的特殊字元,例如 **.NET**。

 如果不存在\<當地語系化名稱>標記,則專案類型由資料夾本身**稱為 SmartPhone2003**。

##### <a name="finding-the-sort-order-for-a-project-type"></a>尋找項目型態的排序順序
 要確定項目類型的排序順序,.vstdir 檔使用\<SortOrder> 標記。

 例如,[CSharp]Windows_Windows.vstdir 檔包含此標記:

```
<SortOrder>5</SortOrder>
```

 [CSharp]資料庫_樣本索引.vstdir 檔具有具有較大值的標記:

```
<SortOrder>5000</SortOrder>
```

 "SortOrder"> 標記中的數位越低,樹中的位置越高,因此**Windows**節點看起來高於**專案類型****Database**\<樹中的資料庫節點。

 如果未\<為項目類型指定 SortOrder>标记,則它按字母順序顯示,\<遵循包含 SortOrder>规范的任何项目类型。

 請注意,"我的文檔(**我的範本**)"資料夾中沒有 .vstdir 檔。 使用者應用程式項目類型名稱未本地化,按字母順序顯示。

#### <a name="a-quick-review"></a>快速回顧
 讓我們修改 **「新項目**」對話方塊並創建新的使用者項目範本。

1. 將 MyProjectNode 子資料夾添加到 [程序文件]微軟可視化工作室 14.0_Common7_IDE_ProjectTemplates_CSharp 資料夾。

2. 使用任何文字編輯器在 MyProjectNode 資料夾中建立 MyProject.vstdir 檔。

3. 將這些行新增到 .vstdir 檔案:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. 保存並關閉 .vstdir 檔案。

5. 使用任何文字編輯器在 MyProjectNode 資料夾中建立 MyProject.vstemplate 檔案。

6. 將這些行新增到 .vstemplate 檔案:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. 保存.vstemplate 檔案並關閉編輯器。

8. 將 .vstemplate 檔案發送到新的壓縮 MyProjectNode_MyProject.zip 資料夾。

9. 從視覺化工作室命令視窗中,鍵入:

    ```
    devenv /installvstemplates
    ```

   開啟 Visual Studio。

10. 打開 **「新項目**」對話方塊並展開視覺化**C#** 專案節點。

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode**顯示為 Windows 節點下的 Visual C++ 的子節點。

## <a name="see-also"></a>另請參閱
- [產生新專案︰深入探討，第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

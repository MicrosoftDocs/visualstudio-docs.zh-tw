---
title: "如何: 建立。Vsct 檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT 檔案建立"
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 建立。Vsct 檔案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

有幾種方式來建立以 XML 為基礎 Visual Studio 命令資料表 \(.vsct\) 組態檔。  
  
-   您可以建立新的 VSPackage 中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 套件\] 範本。  
  
-   您可以使用以 XML 為基礎的命令資料表設定編譯器，Vsct.exe，從現有的.ctc 檔案產生的檔案。  
  
-   您可以使用 Vsct.exe 從現有的.cto 檔案產生.vsct 檔。  
  
-   您可以手動建立新的.vsct 檔。  
  
 本主題說明如何手動建立新的.vsct 檔。  
  
### 若要手動建立新的.vsct 檔案  
  
1.  啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
2.  在 **檔案** 功能表上，指向 **新增**, ，然後按一下 \[ **檔案**。  
  
3.  在 **範本** \] 窗格中，按一下 \[ **XML 檔案** 然後按一下 \[ **開啟**。  
  
4.  在 **檢視** \] 功能表上，按一下 \[ **屬性\] 視窗** ，顯示的 XML 檔案的內容。  
  
5.  在 **屬性** \] 視窗中，按一下 \[瀏覽 \(...\) 結構描述屬性\] 按鈕。  
  
6.  在 XSD 結構描述清單中，選取 \[vsct.xsd 結構描述。 如果不在清單中，按一下 \[ **新增** ，然後尋找 \[本機磁碟機上的檔案。 按一下 \[ **確定** 完畢時。  
  
7.  在 XML 檔案中，輸入 `<CommandTable` 然後按 TAB 鍵。 關閉標記輸入 `>`。  
  
     這會建立基本的.vsct 檔案。  
  
8.  填入您想要新增的 XML 檔案的項目，根據 [VSCT 結構描述](../../extensibility/vsct-xml-schema-reference.md)。 如需詳細資訊，請參閱[\[撰寫中。Vsct 檔案](../../extensibility/internals/authoring-dot-vsct-files.md)。  
  
## 編譯程式碼  
 只要將.vsct 檔加入至專案並不會編譯它。 您必須將其整合建置流程中。  
  
### 若要將.vsct 檔加入至專案編譯  
  
1.  在編輯器中開啟您的專案檔。 如果在載入專案時，您必須先卸載。  
  
2.  新增 [ItemGroup 項目](../../msbuild/itemgroup-element-msbuild.md) ，其中包含了 VSCTCompile 項目，如下列範例所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName 項目必須一律設定為 `Menus.ctmenu`。  
  
3.  如果您的專案包含.resx 檔案，新增 EmbeddedResource 元素包含 MergeWithCTO 項目，如下列範例所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     此標記應該放入包含內嵌的資源的 ItemGroup 項目。  
  
4.  開啟封裝檔案，通常名為 *ProjectName*Package.cs 或 *ProjectName*Package.vb，在編輯器中的。  
  
5.  將 ProvideMenuResource 屬性加入在套件類別，如下列範例所示。  
  
    ```c#  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     第一個參數值必須符合您在專案檔中定義的 ResourceName 屬性的值。  
  
## 請參閱  
 [\[撰寫中。Vsct 檔案](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [如何：從現有的 .ctc 檔建立 .vsct 檔](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [如何：從現有的 .Cto 檔建立 .Vsct 檔](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
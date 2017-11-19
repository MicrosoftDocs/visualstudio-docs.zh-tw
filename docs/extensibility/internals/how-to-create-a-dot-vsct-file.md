---
title: "如何： 建立。Vsct 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f05461aa75a8088f758bd24ec5e73ccd407a8681
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-vsct-file"></a>如何： 建立。Vsct 檔案  
  
有幾種方式來建立以 XML 為基礎 Visual Studio 命令表 (.vsct) 的設定檔。  
  
-   您可以建立新的 VSPackage 中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]封裝範本。  
  
-   您可以使用以 XML 為基礎的命令資料表設定編譯器 Vsct.exe，從現有的.ctc 檔產生的檔案。  
  
-   您可以從現有的.cto 檔產生.vsct 檔使用 Vsct.exe。  
  
-   您可以手動建立新的.vsct 檔。  
  
 本主題說明如何手動建立新的.vsct 檔。  
  
### <a name="to-manually-create-a-new-vsct-file"></a>若要手動建立新的.vsct 檔  
  
1.  啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
2.  在**檔案**功能表上，指向**新增**，然後按一下 **檔案**。  
  
3.  在**範本** 窗格中，按一下  **XML 檔案**，然後按一下 **開啟**。  
  
4.  在**檢視**功能表上，按一下 [**屬性] 視窗**顯示 XML 檔案的屬性。  
  
5.  在**屬性**視窗中，按一下 瀏覽 （...） 按鈕上的結構描述屬性。  
  
6.  在 XSD 結構描述清單中，選取 vsct.xsd 結構描述。 如果不是在清單中，按一下**新增**然後尋找 本機磁碟機上的檔案。 按一下**確定**完畢時。  
  
7.  在 XML 檔案中，輸入`<CommandTable`然後按 TAB 鍵。 關閉標記輸入`>`。  
  
     這會建立基本.vsct 檔。  
  
8.  填入您想要新增的 XML 檔案的項目，根據[VSCT 結構描述](../../extensibility/vsct-xml-schema-reference.md)。 如需詳細資訊，請參閱[撰寫。Vsct 檔案](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>如何：從現有的 .ctc 檔建立 .vsct 檔  
  
您可以從現有命令資料表 .ctc 原始程式檔建立 XML .vsct 檔。 如此一來，您可以利用新的 XML 架構[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令資料表 (VSCT) 編譯器格式。  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>從 .ctc 檔建立 .vsct 檔  
  
1.  取得一份 Perl 語言。  
  
2.  取得一份 Perl 指令碼 ConvertCTCToVSCT.pl，一般位於 *\<Visual Studio SDK 安裝路徑 >*\VisualStudioIntegration\Tools\bin 資料夾。  
  
3.  取得一份您想要轉換的 .ctc 原始程式檔。  
  
4.  將檔案放置在相同的目錄中。  
  
5.  在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令提示字元視窗，瀏覽至目錄。  
  
6.  類型  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     其中，PkgCmd.ctc 是 .ctc 檔的名稱，而 PkgCmd.vsct 是您要建立之 vsct 檔的名稱。  
  
     這會建立新的 .vsct XML 命令資料表原始程式檔。 您可以像是處理任何其他 .vsct 檔一樣，使用 Vsct.exe (VSCT 編譯器) 編譯此檔案。  
  
    > [!NOTE]
    >  您可以重新格式化 XML 註解來改善 .vsct 檔的可讀性。  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>如何：從現有的 .Cto 檔建立 .Vsct 檔  
  
您可以從現有的二進位檔 .cto 建立 XML 檔 .vsct。 這樣做可讓您充分利用新的命令資料表編譯器格式。 即使 .cto 檔是從 .ctc 檔所編譯，這個程序也適用。 您可以將 .vsct 檔編輯並編譯成另一個 .cto 檔。  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>從 .cto 檔建立 .vsct 檔  
  
1.  取得 .cto 檔案和其對應 .ctsym 檔的複本。  
  
2.  將檔案放入與 vsct.exe 編譯器所在相同的目錄。  
  
3.  在 Visual Studio 命令提示字元中，移至包含 .cto 和 .ctsym 檔的目錄。  
  
4.  輸入 **vsct.exe** *ctofilename***.cto** *vsctfilename***.vsct -S***symfilename***.ctsym**。  
  
     `ctofilename`是.cto 檔，名稱`vsctfilename`是您想要建立之 vsct 檔的名稱和`symfilename`是.ctsym 檔的名稱。  
  
     這個程序會建立新的 .vsct XML 命令資料表編譯器檔案。 您可以像是處理任何其他 .vsct 檔一樣，使用 vsct 編譯器 vsct.exe 編輯及編譯此檔案。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 只要將.vsct 檔加入至專案並不會其進行編譯。 您必須在建置流程中加入它。  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>將專案編譯中加入.vsct 檔  
  
1.  在編輯器中開啟您的專案檔。 如果在載入專案時，您必須先卸載。  
  
2.  新增[ItemGroup 項目](../../msbuild/itemgroup-element-msbuild.md)包含 VSCTCompile 項目，如下列範例所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName 元素應一律設`Menus.ctmenu`。  
  
3.  如果您的專案包含.resx 檔，新增 EmbeddedResource 元素包含 MergeWithCTO 項目，如下列範例所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     這個標記應包含內嵌的資源的 ItemGroup 項目內。  
  
4.  開啟封裝檔案，通常名為*ProjectName*Package.cs 或*ProjectName*Package.vb，在編輯器中的。  
  
5.  ProvideMenuResource 將屬性加入至套件類別中，如下列範例所示。  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     第一個參數值必須符合您在專案檔中定義的 ResourceName 屬性的值。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫。Vsct 檔案](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio 命令表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
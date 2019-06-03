---
title: HOW TO：建立。Vsct 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056935"
---
# <a name="how-to-create-a-vsct-file"></a>HOW TO：建立 .Vsct 檔案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

有數種方式可建立 XML 型 Visual Studio Command Table (.vsct) 組態檔。  
  
- 您可以建立新的 VSPackage 中[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]封裝範本。  
  
- 您可以使用以 XML 為基礎的命令資料表設定編譯器 Vsct.exe，從現有的.ctc 檔產生的檔案。  
  
- 您可以使用 Vsct.exe 從現有的.cto 檔產生.vsct 檔。  
  
- 您可以手動建立新的.vsct 檔。  
  
  本主題說明如何以手動方式建立新的.vsct 檔。  
  
### <a name="to-manually-create-a-new-vsct-file"></a>若要手動建立新的.vsct 檔  
  
1. 啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
2. 在上**檔案**功能表上，指向**新增**，然後按一下**檔案**。  
  
3. 在 **範本**窗格中，按一下**XML 檔案**，然後按一下 **開啟**。  
  
4. 在上**檢視**功能表上，按一下**屬性 視窗**，顯示的 XML 檔案的內容。  
  
5. 在 **屬性** 視窗中，按一下 瀏覽 （...） 按鈕，在結構描述屬性。  
  
6. 在 XSD 結構描述的清單中，選取 vsct.xsd 結構描述。 如果它不在清單中，按一下**新增**，然後尋找 本機磁碟機上的檔案。 按一下 **確定**完畢時。  
  
7. 在 XML 檔案中，輸入`<CommandTable`然後按 TAB 鍵。 輸入關閉標記`>`。  
  
     這會建立基本的.vsct 檔。  
  
8. 在 XML 檔案，您想要新增的項目填滿、 根據[VSCT 結構描述](../../extensibility/vsct-xml-schema-reference.md)。 如需詳細資訊，請參閱[撰寫。Vsct 檔案](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 只要將.vsct 檔加入專案不會造成其進行編譯。 您必須將它納入建置流程中。  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>將專案編譯中加入.vsct 檔  
  
1. 在編輯器中開啟您的專案檔。 如果載入專案時，您必須先卸載它。  
  
2. 新增[ItemGroup 項目](../../msbuild/itemgroup-element-msbuild.md)，包含 VSCTCompile 項目，如下列範例所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName 項目應一律設為`Menus.ctmenu`。  
  
3. 如果您的專案包含.resx 檔案，加入 EmbeddedResource 項目，其中包含 MergeWithCTO 項目，如下列範例所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     這個標記應包含內嵌的資源的 ItemGroup 項目內。  
  
4. 開啟封裝檔案，通常名為*ProjectName*Package.cs 或*ProjectName*Package.vb，在編輯器中的。  
  
5. ProvideMenuResource 將屬性加入至套件類別，如下列範例所示。  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     第一個參數值必須符合您在專案檔中定義 ResourceName 屬性的值。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫。Vsct 檔案](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio 命令資料表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [如何：建立。從現有的 Vsct 檔案。Ctc 檔案](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [如何：建立。從現有的 Vsct 檔案。Cto 檔案](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
